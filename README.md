# xoy
Calibration tool for multiple head (IDEX) 3D printers

## Background and purpose
IDEX printers might have their heads not perfectly aligned. This can cause the print with different filament colors or materials to be displaced.
Sovol SV04 for example provides a presliced print for this purpose, but it is quite coumbersome. I watched the [video](https://www.youtube.com/watch?v=wJp_IZqt4BQ&t=4s) on _My Tech Fun_ channel regarding this printer, where the YouTuber spoke about a much simpler method, using a specialized camera built and sold by *Ember Prototypes*, the [Camera-Assisted XY Calibration Tool](https://www.emberprototypes.com/products/cxc), which is a great idea. However, it is just another camera for just one single purpose. Then I realized, that I already have a camera I could use: it is on my phone. I just need to make the video stream available on a web page. Then I stumbled upon the great DroidCam. So, inspired by the features of both tools, I made this simple web application.

My app is heavily relying on the DroidCam, so, make sure to grab it before trying this out. It is available for both Android and iOS. 
The links to both stores are available from their website: https://www.dev47apps.com/

My app can be used with constraints using the free version, but I highly recommend supporting them by buying the full version. It is still much cheaper and is of more use than a single-purpose camera. 

Disclaimer: I have or had no affiliation to either of these.

## Usage
1. Install DroidCam on your phone
0. Start it, go to the settings, and check the HTTPS box.
0. Note the local URL (like: `https://192.168.1.33:4343`).
0. Select the rear camera, but it should be selected by default.
0. Home your printer.
0. Move the first head to the center of the bed using the printer controls.
0. Elevate the heads well above the bed. 10-15cm should suffice for the start. Unfortunately, you won't be able to select the macro lens, even if you have one, hence you are stuck with the capabilities of the main rear camera.
0. Open the hosted version of my app by clicking here: [zorgoz.github.io/xoy/](https://zorgoz.github.io/xoy/index.html). Obviously, you need another device for that, with a browser.
0. The application will ask for the camera stream URL. It will be remembered by the browser, but you can change it anytime. You will need to if your phone has dynamic IP.
0. Once connected, place your phone on the printing bed facing down. I suggest putting something under the phone to allow smooth WiFi communication. I have used a small cardboard box.
0. Position the camera so that you are seeing the cross somewhere in the middle of the nozzle.
0. Adjust the head height and use the autofocus button to get the clearest view possible. You might want to turn the flashlight on.
0. Use the printer controls to position the cross in the absolute center of the nozzle hole. Or as close as possible.
0. Write the coordinates in the inputs of the first row.
0. Change heads. Beware not to change the Z-axis value as the camera lens might not be perpendicular. And of course, don't move the phone on the bed!
0. Repeat the X-Y positioning steps for the second head.
0. Write the coordinates to the inputs in the second row.
0. The _dX_ and _dY_ columns will contain the correction values you need to configure the printer with.

## Troubleshooting
- Because of the self-signed certificate, your browser might refuse to connect to the embedded server at first. Just open the camera stream URL directly once, and proceed to the insecure location. Your next attempt with the app should work.
- If you have the free version of DroidCam, or you have troubles with the HTTPS stream, you have to stick with plain HTTP. But because browser security defaults these days, it will refuse to connect to a non-https endpoint when loaded from a secure host, like github. In this case, you will need to host the application yourself. I made it self-contained, hence it is just a single http file to download: [index.html](https://raw.githubusercontent.com/zorgoz/xoy/main/index.html). You can also simply open it directly in your browser, but local storage won't work there, hence it will ask for the camera stream URL every time.

Have fun printing!
