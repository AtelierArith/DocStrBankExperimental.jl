transformedimagebounds

Find where the corners of an image are transformed to by transform H and return the bounds.

```
Usage:  (minx, maxx, miny, maxy) = transformedimagebounds(img::Array, H::Array)
        (minx, maxx, miny, maxy) = transformedimagebounds(sze::Tuple, H::Array)

Arguments:   img - An array storing the image or
             sze - A tuple giving the size of the image.
               H - The transforming homography, a 3x3 matrix.

Returns:
      minx, maxx - The range of x, y coords (range of column and row coords) of
      miny, maxy   the transformed image.

```
