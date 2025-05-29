```
SplinePSF(psf_stack::AbstractArray{<:Real,3}, 
          x_range::AbstractRange,
          y_range::AbstractRange,
          z_range::AbstractRange;
          order::Integer=3)
```

PSFスタックと座標範囲から3D SplinePSFを構築します。

# 引数

  * `psf_stack`: 次元が[y, x, z]のPSFデータを含む3D配列
  * `x_range`: マイクロメートル単位の均等に間隔を空けたx座標の範囲
  * `y_range`: マイクロメートル単位の均等に間隔を空けたy座標の範囲
  * `z_range`: マイクロメートル単位の均等に間隔を空けたz座標の範囲
  * `order`: 補間の次数（デフォルト: 3は三次Bスプライン）

# 戻り値

  * `SplinePSF`: PSFの3Dスプライン補間

# 例

```julia
# サンプリングされた強度値から3Dスプラインを作成
x_range = y_range = range(-2.0, 2.0, length=41)  # 0.1μm間隔の41×41の横方向サンプル
z_range = range(-1.0, 1.0, length=21)            # 0.1μm間隔の21の軸方向サンプル
psf_values = zeros(Float64, 41, 41, 21)          # PSF値で埋める
spline_psf = SplinePSF(psf_values, x_range, y_range, z_range)
```
