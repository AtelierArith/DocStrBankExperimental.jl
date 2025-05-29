hollow_sphere(obj, radius=0.8, center=sz.÷2 .+1; thickness=0.8)

3Dの空洞球体の表現を作成します。

# 引数

  * `obj`: 球体が追加されるオブジェクトを表す3D配列。
  * `radius`: 球体の半径を表す浮動小数点数。
  * `thickness`: ピクセル単位での球体の厚さを表す浮動小数点数。デフォルトは0.8です。
  * `center`: 球体の中心を表すタプル。デフォルトはオブジェクトの中心です。

# 戻り値

  * `sph::Array{Float64}`: 空洞球体を表す3D配列。

# 例

```jldoctest
# オブジェクトサイズの80%の中心にある球体を厚さ0.8ピクセルで作成
julia> obj = zeros(Float64, (128, 128, 128));
julia> hollow_sphere(obj, 0.8)
```
