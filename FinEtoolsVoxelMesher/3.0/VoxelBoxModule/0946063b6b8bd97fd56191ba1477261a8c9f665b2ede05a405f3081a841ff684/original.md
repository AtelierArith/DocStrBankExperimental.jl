```
resample!(V::VoxelBoxVolume, resize_ratio)
```

Resize the voxel box.

  * `resize_ratio` = if less than one, the voxel will become bigger (subsampling); otherwise the voxels will shrink (super sampling).
