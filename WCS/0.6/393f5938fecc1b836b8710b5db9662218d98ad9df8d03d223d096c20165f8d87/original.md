```
pix_to_world!(wcs, pixcoords, worldcoords[; stat=, imcoords=, phi=, theta=])
```

Convert the array of pixel coordinates `pixcoords` to world coordinates according to the WCSTransform `wcs`, storing the result in the `worldcoords` and `stat` arrays. `pixcoords` should be a 2-d array where "pixcoords[:, i]" is the i-th set of coordinates, or a 1-d array representing a single set of coordinates. `worldcoords` must be the same size and type as `pixcoords`.

If given, the arrays `stat`, `imcoords`, `phi`, `theta` will be used to store intermediate results. Their sizes and types must all match `pixcoords`, except for `stat` which should be the same size but of type Cint (typically Int32).
