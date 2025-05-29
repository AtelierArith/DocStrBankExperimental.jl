```julia
elementdiameter(
    coords::Vector{Vector{Float64}}
) -> Union{Float64, Int64}

```

与えられた座標でスパンされた要素の直径（すなわち、最長のエッジの長さ）を返します。

座標は必ずしも完全な次元の要素をスパンする必要はありません。境界要素にも使用できます。
