```
visualize_flow(flow, ColorBased(), RasterConvention())
visualize_flow(flow, ColorBased(), CartesianConvention())
```

Returns an image that matches the dimensions of the input matrix and that depicts the orientation and magnitude of the optical flow vectors using the HSV color space.

# Details

Hue encodes angle between optical flow vector and the x-axis in the image plane; saturation encodes the ratio between the individual vector magnitudes and the maximum magnitude among the whole motion field, and the values always equal one.

# Arguments

The flow parameter needs to be a two-dimensional arrays of length-2 vectors (of type SVector) which represent the displacement of each pixel. The displacement can be expressed in a coordinate system based on a RasterConvention() (i.e. rows and columns of a matrix) or a CartesianConvention().

# Example

Compute the HSV encoded visualization of flow vectors in (row, column) convention.

```julia

using ImageTracking

hsv = visualize_flow(flow, ColorBased(), RasterConvention())

imshow(RGB.(hsv))
```

Compute the HSV encoded visualization of flow vectors in (x, y) convention.

```julia

using ImageTracking

hsv = visualize_flow(flow, ColorBased(), CartesianConvention())

imshow(RGB.(hsv))
```

# References

[1] S. Baker, D. Scharstein, JP Lewis, S. Roth, M.J. Black, and R. Szeliski. A database and evaluation methodology for optical flow. International Journal of Computer Vision, 92(1):1–31, 2011.
