imerode - 2D morphological erosion with rectangular or octagonal structing element

```
Usage: eimg = imerode(img, seType, seSize)

Arguments: img - Image to be eroded
        seType - String either "rectangle" or "octagon" specifying the
                 structuring element type. Can be shortened to "rect" or
                 "oct".
        seSize - Structuring element size.
                 If the seType is 'rect' seSize can be a 2 element vector
                 indicating the size of the rectangular structuring element
                 [rows, cols], or if it is a single value the structuring
                 element is square [seSize x seSize]
                 If seType is 'oct' then seSize is the nominal radius of
                 the octagonal structuring element.

Returns:  eimg - The eroded image.
```

Note that the radius of the octagonal structuring element is somewhat nominal due to discrete approximations.  If anything the structuring element may end up with a slightly larger radius than specified rather than being smaller.

This function uses Marcel van Herk's algorithm to run in linear time with respect to the size of the image, irrespective of the structing element size.

See also imdilate(), erode1d(), dilate1d()
