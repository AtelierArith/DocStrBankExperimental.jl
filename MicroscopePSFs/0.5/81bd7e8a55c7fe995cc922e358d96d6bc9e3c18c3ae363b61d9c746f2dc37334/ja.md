```
SplinePSF(psf::AbstractPSF, 
          x_range::AbstractRange, 
          y_range::AbstractRange,
          z_range::AbstractRange;
          order::Integer=3)
```

既存のPSFを定期的なグリッドでサンプリングして3D SplinePSFを作成します。

# 引数

  * `psf`: サンプリングするソースPSF
  * `x_range`: マイクロメートル単位でサンプリングするx座標の範囲
  * `y_range`: マイクロメートル単位でサンプリングするy座標の範囲
  * `z_range`: マイクロメートル単位でサンプリングするz座標の範囲
  * `order`: 補間の次数（デフォルト: 3は三次）

# 戻り値

  * `SplinePSF`: サンプリングされたPSFのスプライン補間

# 例

```julia
# 4µmの範囲で1µmの間隔を持つScalarPSFからスプラインを作成
scalar_psf = ScalarPSF(1.4, 0.532, 1.518)  # NA=1.4, λ=532nm, n=1.518
x_range = y_range = range(-2.0, 2.0, length=41)
z_range = range(-1.0, 1.0, length=21)
spline_psf = SplinePSF(scalar_psf, x_range, y_range, z_range)
```
