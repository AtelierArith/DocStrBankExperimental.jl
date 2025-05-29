```julia
nanbinmedian(x, y, xedges::AbstractRange)
```

`xedges`で指定されたビンエッジに沿った`x`軸の各`length(xedges)-1`の等間隔ビンに入る`y`値の中央値を計算します。`NaN`は無視されます。

`y`が2次元配列（行列）の場合、各列は別々の変数として扱われます。

## 例

```julia
julia> nanbinmedian([1:100..., 1], [1:100..., NaN], 0:25:100)
4-element Vector{Float64}:
 12.5
 37.0
 62.0
 87.0

julia> nanbinmedian(1:100, reshape(1:300,100,3), 0:25:100)
4×3 Matrix{Float64}:
 12.5  112.5  212.5
 37.0  137.0  237.0
 62.0  162.0  262.0
 87.0  187.0  287.0
```
