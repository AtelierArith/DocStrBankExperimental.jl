mapimage2plane! - Projects an image onto a plane in 3D

```
Usage:  mapimage2plane!(mappedimg, rect3Dpts, img, P)

Arguments:
       mappedimg - Buffer for storing the resulting projected image. ::Array{Float64,2}
          rect3D - 3x4 array specifying the 3D coordinates of the four
                   corners of the image rectangle. Points are ordered
                   clockwise from the top-left corner.
             img - Image to be projected. ::Array{Float64,2}
               P - 3x4 projection matrix for img.

```

The four 3D points specifying the corners of the rectangle in the plane are projected into the image to obtain their corresponding image coordinates.  A homography is computed between these points and the corner coordinates of the mappedimage buffer.  This is then applied to img to project it into mappedimg.
