imagecorners2plane - Get the positions of image corners projected onto a plane.

```
Usage: pt = imagecorners2plane(C, planeP, planeN)

Arguments:
        C - Camera structure or 3x4 projection matrix.
   planeP - 3-vector defining a point on the plane.
   planeN - 3-vector defining the normal of the plane.

Returns:
        pt - 3x4 array of 3D points on the plane that the image corners
             project to. Points are orderer clockwise from the top-left
             corner of the image.

```

See also: imagept2plane()
