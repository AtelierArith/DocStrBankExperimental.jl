solvestereopt - Homogeneous linear solution of a stereo point

```
Usage:
        pt = solvestereopt(xy, P)
        pt = solvestereopt(xy, C)
        (pt, xy_reproj) = solvestereopt(xy, P, reprojecterror=true)
        (pt, xy_reproj) = solvestereopt(xy, C, reprojecterror=true)

Multiview stereo: Solves 3D location of a point given image coordinates of
that point in two, or more, images.

Arguments:    xy - 2xN matrix of x, y image coordinates, one column for
                   each camera.
               P - N array of corresponding 3x4 image projection
                   matrices, or
               C - An N array of Camera structures
  reprojecterror - Boolean flag indicating whether reprojection errors should be retunred.

Returns:      pt - 3D location in space returned in normalised
                   homogeneous coordinates (a 4-vector with last element = 1)
       xy_reproj - 2xN matrix of reprojected image coordinates.
```

See also: idealimagepts(), camstruct2projmatrix(), Camera()
