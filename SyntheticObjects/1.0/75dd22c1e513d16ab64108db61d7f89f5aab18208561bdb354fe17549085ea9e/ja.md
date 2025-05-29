```
draw_sphere!(arr, radius, center; thickness=0.8, intensity=one(eltype(arr)))
```

3D配列にガウスプロファイルを追加することで球体を描画します。

# 引数:

  * `arr::Array`: 球体が追加される3D配列。
  * `radius`: 数またはタプルとしての球体の半径。
  * `center`: タプルとしての球体の中心。デフォルト: size(arr).÷2 .+1 で、配列の中心からの（右下）ピクセルです。
  * `thickness`: 球体の厚さ。デフォルトは0.8。
  * `intensity::Float64`: 球体の強度。デフォルトは1.0。

# 例

```jldoctest
julia> arr = zeros(Float32, (128, 128, 128));
julia> draw_sphere!(arr, 10);

julia> draw_sphere!(arr, (20,30,40), (50,30,80));
```
