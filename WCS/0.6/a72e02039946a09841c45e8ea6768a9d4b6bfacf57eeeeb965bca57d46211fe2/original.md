```
world_to_pix!(wcs, worldcoords, pixcoords[; stat=, phi=, theta=, imcoords=])
```

Convert the array of pixel coordinates `worldcoords` to pixel coordinates according to the WCSTransform `wcs`, storing the result in the `pixcoords` array. `worldcoords` should be a 2-d array where "worldcoords[:, i]" is the i-th set of coordinates, or a 1-d array representing a single set of coordinates. `pixcoords` must be the same size and type as `worldcoords`.

If given, the arrays `stat`, `imcoords`, `phi`, `theta` will be used to store intermediate results. Their sizes and types must all match `worldcoords`, except for `stat` which should be the same size but of type Cint (typically Int32).
