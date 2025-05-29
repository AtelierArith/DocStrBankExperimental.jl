```
cameramap()
cameramap(scale)
cameramap(scale, offset)
```

Create a transformation that takes points in real space (e.g. 3D) and projects them through a perspective transformation onto the focal plane of an ideal (pinhole) camera with the given properties.

The `scale` sets the scale of the screen. For a standard digital camera, this would be `scale = focal_length / pixel_size`. Non-square pixels are supported by providing a pair of scales in a tuple, `scale = (scale_x, scale_y)`. Positive scales represent a camera looking in the +z axis with a virtual screen in front of the camera (the x,y coordinates are not inverted compared to 3D space). Note that points behind the camera (with negative z component) will be projected (and inverted) onto the image coordinates and it is up to the user to cull such points as necessary.

The `offset = (offset_x, offset_y)` is used to define the origin in the imaging plane. For instance, you may wish to have the point (0,0) represent the top-left corner of your imaging sensor. This measurement is in the units after applying `scale` (e.g. pixels).

(see also [`PerspectiveMap`](@ref))
