idealimagepts - Ideal image points with no distortion.

```
Usage:  xyideal = idealimagepts(C, xy)

Arguments:
         C - Camera structure
        xy - Image points specified as 2 x N array (x,y) / (col,row)

Returns:
   xyideal - Ideal image points.  These points correspond to the image
             locations that would be obtained if the camera had no lens
             distortion.  That is, if they had been projected using an ideal
             projection matrix computed from fx, fy, ppx, ppy, skew.
```

See also Camera(), cameraproject()
