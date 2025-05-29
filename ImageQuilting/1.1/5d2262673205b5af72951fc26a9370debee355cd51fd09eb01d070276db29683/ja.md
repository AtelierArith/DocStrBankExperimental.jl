```
voxelreuseplot(trainimg; [options])
```

`trainimg`の平均ボクセル再利用プロット。

## 利用可能なオプション:

  * `tmin`    - 最小タイルサイズ（デフォルトは`7`）
  * `tmax`    - 最大タイルサイズ（デフォルトは`minimum(size(trainimg))`）
  * `overlap` - オーバーラップの割合（デフォルトはタイルサイズの1/6）
  * `nreal`   - 実現の数（デフォルトは10）
  * `rng`     - 擬似乱数生成器（デフォルトは`Random.default_rng()`）
