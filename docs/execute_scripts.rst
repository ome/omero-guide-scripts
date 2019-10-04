**Run server-side scripts**
===========================

The server-side Python scripts on OMERO give an opportunity to run the analysis close to the data.

**Description**
---------------

The server-side Python scripts on OMERO can be accessed via both the OMERO.web and OMERO.insight user interfaces. The scripts are typically uploaded by an administrator or a restricted administrator of the OMERO.server and can be run by any user on the server.

First, two examples are presented showing the experience from the user interface of OMERO.web (Batch ROI export and Kymograph).

Second, the process of writing, uploading and editing of OMERO script is explored

**Setup**
---------

No specific setup needed.

**Resources**
-------------

-  Images for the Batch ROI Export.py script see \ https://downloads.openmicroscopy.org/images/DV/siRNAi-HeLa/

-  Images for Kymograph script were downloaded from \ http://jcb.rupress.org/content/194/2/187\ .(Bowen et. al. Journal of Cell Biology 194 (2): 187).

-  The simple example script is available on \ https://raw.githubusercontent.com/ome/training-scripts/master/practical/python/server/hello_world.py

**Step-by-Step**
----------------

Example:
~~~~~~~~

#.  We will now analyse the ROIs created in OMERO.iviewer using a server-side script.

#.  Go to the siRNA-HeLa Dataset and open several images whose name start with VRAQ… in OMERO.iviewer.

#.  We want to measure the distance between Centromeres, stained with ACA in the 4th Channel. Turn on ONLY the 4th channel and open the ROIs tab to on the right-hand pane.

#.  Draw several lines between the centromeres as indicated on the screenshot below. \ |image1a|

#.  Try to identify centromere pairs:

    - Select the Line tool and draw a line between the centres of the centromeres.

    - In the ROIs table, in the Comments column, click the 3 dots in the column header and choose to Show Area/Length.

#.  Do the same now on several of the Images whose names start with IN..., which are in the Metaphase state.

#.  Select Dataset siRNA-HeLa.

#.  Click the Script button in the top-right of the page \ |image2a|\ .

#.  Select export_scripts > Batch_ROI_Export…

#. In the dialog that pops up, click on View Script to view the Python code.

#. Search for "\ idr\ "# to find the code block that selects the filter_channel based on Dataset and Channel names.

#. Scroll to the bottom of the script to see where the input parameters are defined, such as Data_Type and IDs. Note how these appear in the script dialog and are auto-populated with the currently-selected Datasets or Images.

    .. image:: images/scripts3.png

#. The script will process all the Images in the selected Dataset and data can be exported as CSV file, with one table row per Shape/Channel.

#. Click Run Script.

#. The status of the processing is displayed in the Activities dialog |image4a|\ .

#. When the script has completed, it will show in the Activities dialog and allow you to download the CSV file. Download this and open it, e.g. in Excel, to see the output data for all the shapes.

Example:
~~~~~~~~

We will now use another server-side script for creating a Kymograph from an Image in OMERO. The Image we will use for the Kymograph demonstration has been published in a study investigating protein migration along microtubules \ http://jcb.rupress.org/content/194/2/187\ .(Bowen et. al.
Journal of Cell Biology 194 (2): 187).

#. Go to the Dataset Kymograph.

#. Select the Image inside the Dataset.

#. Double-click to open the Image in OMERO.iviewer and draw one or more lines along microtubules which seems to have the most persistent trafficking of objects along them.

#. Save the line(s).

#. Go back to the webclient. Click the Script button in the top-right of the page\ |image2a|\ .

    .. image:: images/scripts5.png


#.  Select workshop_scripts > Kymograph...

#.  The script will create a new image (=Kymograph) where the pixels under the line region you have drawn previously will be collated into this image timepoint by timepoint. The row of pixels from the first timepoint will be on the top of the new Kymograph Image.

#.  Note: the direction in which you have drawn the line ROI on the original image matters with respect to the orientation of the stripes composing the Kymograph image. The start of the original line is on the left of the Kymograph Image, the end on the right.

#.  Open the new Kymograph image in OMERO.iviewer.

#. Find some tracks (typically red stripes going under angles across the image, see screenshot below).

    .. image:: images/scripts6.png
         :width: 1.58333in
         :height: 2.84896in
    .. image:: images/scripts7.png
         :width: 1.53646in
         :height: 2.83333in

#. Draw some lines over these tracks and save them.

#. Go back to the webclient, select the Kymograph Image and select the script analysis > Kymograph analysis...

#. Run this script. The Kymograph analysis script will produce a CSV file attachment on the Kymograph Image.

#. Open the CSV in Excel for example and verify the speeds of the observed particles in the original image.


.. |image1a| image:: images/scripts1.png
   :width: 5.9975in
   :height: 3.64063in
.. |image2a| image:: images/scripts2.png
   :width: 0.36621in
   :height: 0.27231in
.. |image3a| image:: images/scripts3.png
   :width: 3.83333in
   :height: 5.04167in
.. |image4a| image:: images/scripts4.png
   :width: 0.25391in
   :height: 0.20833in

