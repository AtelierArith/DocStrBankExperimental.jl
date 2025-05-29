```
vox(f::NIVolume, args...,)
```

Get the value of a voxel from volume `f`, scaled by slope and intercept given in header, with 0-based indexing. `args` are the voxel indices and the length should be the number of dimensions in `f`.
