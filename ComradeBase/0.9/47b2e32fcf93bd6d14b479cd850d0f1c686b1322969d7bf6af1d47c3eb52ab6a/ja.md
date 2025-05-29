```
imagepixels(fovx, fovy, nx, ny, x0=0, y0=0; posang=0.0, executor=Serial(), header=NoHeader())
```

フィールドオブビュー `fovx` と `fovy`、および `nx` と `ny` ピクセルを持つピクセルのグリッドを構築します。これらの点はピクセルの中心であり、フィールドオブビューは最初のピクセルの端から最後のピクセルの端まで広がります。`x0` と `y0` のオフセットは、画像平面内で画像の原点を (`x0`, `y0`) だけシフトします。

## 引数:

  * `fovx::Real`: x方向のフィールドオブビュー
  * `fovy::Real`: y方向のフィールドオブビュー
  * `nx::Integer`: x方向のピクセル数
  * `ny::Integer`: y方向のピクセル数

## キーワード引数:

  * `x0::Real=0`: 画像のxオフセット
  * `y0::Real=0`: 画像のyオフセット
  * `posang::Real=0`: RA=0軸に対するグリッドの位置角。
  * `executor=Serial()`: グリッドに使用するエグゼキュータ、デフォルトはシリアル実行
  * `header=NoHeader()`: グリッドに使用するヘッダー
