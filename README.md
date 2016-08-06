# Demo
[![IMAGE ALT TEXT HERE](http://img.youtube.com/vi/V4fI7awhCKA/0.jpg)](http://www.youtube.com/watch?v=V4fI7awhCKA)

# kendo-UI-Mobile-Touch-Two-Fingers-Pinch-gestures
This is a Hyprid Telerik Platform Kendo UI Mobile App Demo: Touch with two fingers to resize the text using Pinch gestures (Pinch to Zoom or Pinch to resize text)
Tested on iOS and Android

# How to configure and run
1. You need a http://www.telerik.com/platform account
2. I use AppBuilder Windows client http://www.telerik.com/platform/appbuilder/windows-client
3. Click on create "+New" project, then "Advance", then "Clone Repository"
4. Insert the following URI "https://github.com/owidat/kendo-UI-Mobile-Touch-Two-Fingers-Pinch-gestures"
5. Choose a name for you project, then click on "Clone" Button

Read: "Clone from Version Control" http://docs.telerik.com/platform/appbuilder/cordova/creating-your-app/clone-from-git

# Documentation
Please visit the following for more documentation on Kendo UI Touch widget, Multi-Touch Gestures, Touch Events, ...
http://docs.telerik.com/kendo-ui/controls/hybrid/styles/touch#multi-touch-gestures

# Code:
All what I did after contacting Telerik support is reading the doc and writing the following code:

Code can be found under "components" > "homeView" > "index.js"


<pre><code>

var pinchStart = 0, pinchMoving = 0, dis = 0;
        
var fontSize = 20, maxFontSize = 50, minFontSize = 15;
        
$("#touch").kendoTouch({
        multiTouch: true,
        gesturestart: function (e) {
            pinchStart = e.distance;
        },
        gesturechange: function (e) {
            pinchMoving = e.distance;
 
            if (pinchStart !== 0) {
                dis = pinchMoving - pinchStart;
                if (dis > 0) {
					$("#result").html("Distanse is growing: " + dis);
                }
                if (dis < 0) {
					$("#result").html("Distanse is shrinking: " + dis);
                }
            }
            fontSize = fontSize + (dis / 10);
            if (fontSize < minFontSize) {
                fontSize = minFontSize; 
            }
            if (fontSize > maxFontSize) {
                fontSize = maxFontSize; 
            }
            $("#touch").css('font-size' , fontSize + 'px');
        },
        gestureend: function (e) {
            console.log("Must save the new font size, which is = " + fontSize);
        }
});
</code></pre>
