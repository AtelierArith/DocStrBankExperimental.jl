```
world_to_pix(wcs, worldcoords)
```

Convert the array of world coordinates `worldcoords` to pixel coordinates according to the WCSTransform `wcs`. `worldcoords` is a 2-d array where "worldcoords[:, i]" is the i-th set of coordinates, or a 1-d array representing a single set of coordinates.

The return value is the same size as `worldcoords`.
