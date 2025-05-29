```
gridpoints_in_polygon(poly::AbstractArray{<:AbstractPolygon},
    grid_x::AbstractArray, grid_y::AbstractArray)
```

ポリゴン `poly` 内にある点に対して `true` を返す `BitArray` を返します。

`BitArray` の値は、左下から始まる点 `(x, y)` に対応し、`x ∈ grid_x`、`y ∈ grid_y` です。

すべてのポリゴンは同じ向き（時計回りまたは反時計回り）である必要があります。混合（例えば「穴」を表すために）は、ポリゴンまたは穴のエッジで望ましい動作をしない可能性があります。
