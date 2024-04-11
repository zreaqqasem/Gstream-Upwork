# Integrating GStreamer into Your Swift Project

## Setting up GStreamer

1. **Install GStreamer Framework:**
   Download and install the GStreamer framework system-wide from [GStreamer official website](https://gstreamer.freedesktop.org/data/pkg/ios/). Follow the installation instructions provided.

2. **Add Initialization Files:**
   Incorporate `gst_ios_init.h` and `gst_ios_init.m` files from the provided project into your Xcode project.

3. **Configure Plugin Settings:**
   Customize plugin settings as needed in the `gst_ios_init.h` file to enable or disable specific plugins for your project.

4. **Create Bridging Header:**
   If you don't have an existing bridging header file, create one. Add the line `#import "gst_ios_init.h"` to the bridging header file.

5. **Configure Project Settings:**
   - Add the bridging header file path in the Objective-C Bridging Header setting of your project.
   - Add the GStreamer framework headers path to the Header Search Path.
   - Add the GStreamer framework path to the Framework Search Path.
   - Add `-lresolv` and `-lc++` to Other Linker Flags.

6. **Add Required Frameworks:**
   Add necessary frameworks and libraries to your project's target, including GStreamer.framework, libiconv.tbd, and others listed in the provided instructions.

7. **Initialize GStreamer:**
   Call `gst_ios_init()` in the `application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions)` method.

## Using GStreamer in Your App

### Sample App Integration
1. **Add Required Files:**
   Include the provided files (`GStreamerBackend.h`, `GStreamerBackend.m`, `GStreamerBackendDelegate.h`, `GStreamerVideoViewController.swift`) to your Xcode project.

2. **Update Bridging Header:**
   Add `#include "GStreamerBackend.h"` to your bridging header file.

3. **Display RTSP Stream:**
   Use the following code snippet in your ViewController's `viewDidLoad` method to display an RTSP stream:
   ```swift
   let videoViewController = GStreamerVideoViewController()
   videoViewController.changeURI(uri)
   view.addSubview(videoViewController.view)
   
   // Auto layout constraints
   videoViewController.view.translatesAutoresizingMaskIntoConstraints = false
   videoViewController.view.topAnchor.constraint(equalTo: view.topAnchor, constant: 0).isActive = true
   videoViewController.view.bottomAnchor.constraint(equalTo: view.bottomAnchor, constant: 0).isActive = true
   videoViewController.view.leftAnchor.constraint(equalTo: view.leftAnchor, constant: 0).isActive = true
   videoViewController.view.rightAnchor.constraint(equalTo: view.rightAnchor, constant: 0).isActive = true
   ```

4. **Provide RTSP Stream URI:**
   Replace `uri` with your desired RTSP stream URL (e.g., `rtsp://wowzaec2demo.streamlock.net/vod/mp4:BigBuckBunny_115k.mov`).

By following these steps, you can seamlessly integrate GStreamer into your Swift project and incorporate RTSP stream playback functionality.

