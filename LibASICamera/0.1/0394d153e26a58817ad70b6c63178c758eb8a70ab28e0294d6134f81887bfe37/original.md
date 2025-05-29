```
set_roi_format(id::Integer, width, height, binning, img_type::ASI_IMG_TYPE)
```

Sets the region of interest (roi). Do so before capturing.

The width and height are the values *after* binning, i.e. you need to set the width to 640 and the height to 480 if you want to run at 640x480 @ BIN2.

ASI120's data size must be a multiple of 1024 which means width*height%1024==0.

# Args:

```
id: Camera id
width: ROI width
height: ROI height
binning: The binning mode; 2 means to read out 2x2 pixels together. Check
    which binning values are supported in the ASI_CAMERA_INFO struct of the
    camera struct or by calling get_camera_property(id).
```

# Throws:

```
ASIError
```
