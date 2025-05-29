```
SplinePSF{T<:AbstractFloat, IT<:AbstractInterpolation} <: AbstractPSF
```

Bスプライン補間として表現された点拡散関数（PSF）。

# フィールド

  * `spline`: Bスプライン補間オブジェクト
  * `x_range`: 一様グリッド補間に使用されるx座標の範囲
  * `y_range`: 一様グリッド補間に使用されるy座標の範囲
  * `z_range`: 3D PSFのz座標の範囲、または2D PSFの場合は`nothing`
  * `original_grid`: 補間を作成するために使用された元のグリッドデータ
  * `interp_order`: 使用される補間次数（0=定数、1=線形、3=三次）

# 注意事項

  * 座標と範囲は物理単位（通常はマイクロメートル）で表されます
  * PSF値はサンプリングされた元のPSFから保持されます
  * 完全な実装はspline_psf.jlにあります
