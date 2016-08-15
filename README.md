# PaveMaint
####Pavement maintenance history for WVC owned streets.  
--------------------------------------------------  
##Components:  
+  Pavement Polygons
+  Treatment Polygons
+  Treatments Table
+  LTAP Table  

###Pavement Polygons
The pavement polygons were created by Erik Brondum by tracing subdivision plans.  It needs to be updated continually as new construction happens.  Current as of 2016.

+  Split @ intersections
+  Split @ subdivision boundaries
+  split @ turns
+  Joined with subdivision data to incorporate year of construction
+  State/Private roads ignored
+  Joined with centerline data prepared for LTAP surveys  
+  Each pavement section is assigned a GUID

 
###Treatments Polygons  
The treatment polygons are a collection of annual treatments to different sections of pavement.  It is used as a visual reference, as the same data is included in the treatments table that is related to the pavement polygons.  
+  Created from CAD data (CAD --> KMZ --> KML --> SHP --> GDB)
+  Bid details are scraped from the Bid summaries using [Tabula](http://tabula.technology/ "Tabula") and then compiled in Excel.  Later saved out as a dBASE table into the GDB.   


###Treatments Table
The treatments table contains the same data as the treatment polygons but it includes the matching GUIDs from the pavement polygons for each section of pavement included in the treatment.  Thus the treatment table has many records for each individual treatment, each corresponding to a different section of pavement.  
+  Join on GUID with pavement polygons  
+  Split pavement when necessary and alter GUID to keep it unique  
+  Add record in treatment table for each section of pavement included in treatment  
+  Include Bid ID (Treatment Year - Bid #)  

###LTAP
LTAP surveys are used to assess the condition of all the public streets in WVC.  Photos are included of each street (1 per street at this point).  In the future request LTAP to enable GPS data on cameras so photos can be plotted as points on map.

+  Join the LTAP data on the Photo #.  This is accomplished by working with the street centerline shapefile they return to WVC.  
+  Create a field for the hyperlink to the photos and enable hyperlinks.  Possible to host through ArcGIS Online but difficult to work with.  Currently pictures are being hosted on internal server.

