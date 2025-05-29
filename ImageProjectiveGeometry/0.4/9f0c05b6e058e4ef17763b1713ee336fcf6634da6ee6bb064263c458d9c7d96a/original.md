imagept2plane - Project image points to a plane and return their 3D locations

```
Usage:  pt = imagept2plane(C, xy, planeP, planeN)

Arguments:
         C - Camera structure, Alternatively
             C can be a 3x4 camera projection matrix.
        xy - Image points specified as 2 x N array (x,y) / (col,row)
    planeP - Some point on the plane.
    planeN - Plane normal vector.

Returns:
        pt - 3xN array of 3D points on the plane that the image points
             correspond to.
```

Note that the plane is specified in terms of the world frame by defining a 3D point on the plane, planeP, and a surface normal, planeN.

Lens distortion is handled by using the standard lens distortion parameters assuming locally that the distortion is constant, computing the forward distortion and then subtracting the distortion.

See also Camera(), cameraproject()
