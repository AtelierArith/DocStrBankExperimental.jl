```
set_roi_start(id::Integer, startx, starty)
```

Sets the position of the top-left corner of the region of interest.

You can call this while the camera is streaming to move the ROI. By default, the ROI will be centered. In binned mode, the start values are relative to the binned sensor size.

# Throws:

```
ASIError
```
