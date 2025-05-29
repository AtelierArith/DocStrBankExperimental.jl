```
SplinePSF(psf_stack::AbstractArray{<:Real,2}, 
          x_range::AbstractRange,
          y_range::AbstractRange;
          order::Integer=3)
```

PSFスタックと座標範囲から2D SplinePSFを構築します。

# 引数

  * `psf_stack`: 次元が[y, x]のPSFデータを含む2D配列
  * `x_range`: マイクロメートル単位の均等に間隔を空けたx座標の範囲
  * `y_range`: マイクロメートル単位の均等に間隔を空けたy座標の範囲
  * `order`: 補間の次数（デフォルト: 3は三次Bスプライン）

# 戻り値

  * `SplinePSF`: PSFの2Dスプライン補間

# 例

```julia
# グリッド上でサンプリングされたエアリPSFから2Dスプラインを作成
x_range = y_range = range(-2.0, 2.0, length=101)  # 101×101グリッド、40nm間隔
airy = AiryPSF(1.4, 0.532)  # NA=1.4, λ=532nm
psf_values = [airy(x, y) for y in y_range, x in x_range]
spline_psf = SplinePSF(psf_values, x_range, y_range)
```
