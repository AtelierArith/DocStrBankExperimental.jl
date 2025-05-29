```
voxelreuseplot(trainimg; [options])
```

Mean voxel reuse plot of `trainimg`.

## Available options:

  * `tmin`    - minimum tile size (default to `7`)
  * `tmax`    - maximum tile size (default to `minimum(size(trainimg))`)
  * `overlap` - the percentage of overlap (default to 1/6 of tile size)
  * `nreal`   - number of realizations (default to 10)
  * `rng`     - random number generator (default to `Random.default_rng()`)
