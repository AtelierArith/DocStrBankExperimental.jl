```
threshold!(V::VoxelBoxVolume, threshold_value, voxel_below, voxel_above)
```

データをしきい値処理します。

データは、`threshold_value`以下の場合は`voxel_below`に設定され、それ以外の場合は`voxel_above`に設定されます。
