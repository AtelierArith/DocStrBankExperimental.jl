```
resample!(V::VoxelBoxVolume, resize_ratio)
```

ボクセルボックスのサイズを変更します。

  * `resize_ratio` = 1未満の場合、ボクセルは大きくなります（サブサンプリング）；それ以外の場合、ボクセルは小さくなります（スーパサンプリング）。
