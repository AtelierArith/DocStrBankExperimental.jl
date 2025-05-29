hollow_sphere([DataType], sz= (128, 128, 128), radius=0.8, center=sz.÷2 .+1; thickness=0.8)

3Dの中空球の表現を作成します。

# 引数

  * `DataType`: 出力配列のオプションのデータ型。デフォルトはFloat32です。
  * `sz`: 球のサイズを表す整数のベクトル。
  * `radius`: 球の半径を表す浮動小数点数。
  * `thickness`: ピクセル単位での球の厚さを表す浮動小数点数。デフォルトは0.8です。
  * `center`: 球の中心を表すタプル。デフォルトはオブジェクトの中心です。

# 戻り値

  * `sph::Array{Float64}`: 中空球を表す3D配列。

# 例

```jldoctest
# オブジェクトサイズの80%の中心にある球を厚さ0.8ピクセルで作成
julia> hollow_sphere()
```
