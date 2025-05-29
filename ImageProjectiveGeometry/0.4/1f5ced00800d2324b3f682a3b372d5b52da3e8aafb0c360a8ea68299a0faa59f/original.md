imagept2ray! - Compute viewing ray corresponding to an image point.

```
Usage:  ray = imagept2ray!(ray, C, x, y)

Arguments:
       ray - 3-vector to store the result.
         C - Camera structure, Alternatively
             C can be a 3x4 camera projection matrix.
      x, y - Image point  (col,row)

Returns:
       ray - 3-vector corresponding to the image point
```

Lens distortion is handled by using the standard lens distortion parameters assuming locally that the distortion is constant, computing the forward distortion and then subtracting the distortion.

See also imagept2ray(), Camera(), cameraproject()
