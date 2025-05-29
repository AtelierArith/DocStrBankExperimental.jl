```
(psf::SplinePSF)(x::Real, y::Real, z::Real)
```

位置 (x, y, z) で 3D スプライン PSF を評価します。

# 引数

  * `x, y, z`: PSF 中心に対するマイクロメートル単位の座標

# 戻り値

  * 指定された位置での PSF 強度

# 注意事項

  * 位置が PSF 境界の外にある場合は 0 を返します
  * 元の PSF データの正規化を保持します

# 例

```julia
# 特定の点で 3D SplinePSF を評価する
intensity = spline_psf(0.1, 0.2, 0.3)
```
