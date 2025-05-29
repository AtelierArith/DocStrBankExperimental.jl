```
threshold!(V::VoxelBoxVolume, threshold_value, voxel_below, voxel_above)
```

Threshold the data.

The data is set to `voxel_below` if the data is below or equal to `threshold_value`; otherwise it is set to `voxel_above`.
