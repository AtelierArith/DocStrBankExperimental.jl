```julia
nanbinmean(x, y, xedges::AbstractRange)
```

`NaN`を無視して、`x`軸に沿った`length(xedges)-1`の等間隔のビンに入る`y`値の平均を計算します。ビンの境界は`xedges`で指定されます。

`x`データの配列は一次元配列（AbstractVectorの任意のサブタイプ）として与えられ、`y`は1次元または2次元配列（AbstractVecOrMatの任意のサブタイプ）として与えられます。`y`が2次元配列の場合、`y`の各列は別々の変数として扱われます。

## 例

```julia
julia> nanbinmean([1:100..., 1], [1:100..., NaN], 0:25:100)
4-element Vector{Float64}:
 13.0
 38.0
 63.0
 87.5

julia> nanbinmean(1:100, reshape(1:300,100,3), 0:25:100)
4×3 Matrix{Float64}:
 13.0  113.0  213.0
 38.0  138.0  238.0
 63.0  163.0  263.0
 87.5  187.5  287.5
```
