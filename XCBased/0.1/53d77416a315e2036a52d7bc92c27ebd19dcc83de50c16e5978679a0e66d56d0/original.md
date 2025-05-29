```
XCBScreen
```

Data about an X screen. The struct has the following fields:

  * `root` – the root window of the screen
  * `default_colormap` – the default colormap of the screen
  * `white_pixel` – the white pixel value for the screen
  * `black_pixel` – the black pixel value for the screen
  * `current_input_masks` – the bitmask of the current input mask for the screen
  * `width_in_pixels` – screen width in pixels
  * `height_in_pixels` – screen height in pixels
  * `width_in_millimeters` – screen width in millimeters
  * `height_in_millimeters` – screen height in millimeters
  * `min_installed_maps` – the number of maps that can be guaranteed to be installed simultaneously, regardless of the number of entries allocated in each map
  * `max_installed_maps` – the maximum number of maps that might possibly be installed simultaneously, depending on their allocations
  * `root_visual` – the visual of the root window of the screen
  * `backing_stores` – indicates when the server supports backing stores for this screen (one of `XCB_BACKING_STORE_NOT_USEFUL`, `XCB_BACKING_STORE_WHEN_MAPPED`, and `XCB_BACKING_STORE_ALWAYS`)
  * `save_unders` – whether the server can support the save-under mode in CreateWindow and ChangeWindowAttributes
  * `root_depth` – the depth of the root window of the scren
  * `allowed_depths` – a `Dict` mapping allowed depths to their [`XCBVisualType`](@ref)s.
