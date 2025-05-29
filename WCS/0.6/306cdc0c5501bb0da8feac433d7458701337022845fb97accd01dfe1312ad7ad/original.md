```
pix_to_world(wcs, pixcoords)
```

Convert the array of pixel coordinates `pixcoords` to world coordinates according to the WCSTransform `wcs`. `pixcoords` should be a 2-d array where "pixcoords[:, i]" is the i-th set of coordinates, or a 1-d array representing a single set of coordinates.

The return value is the same shape as `pixcoords`.
