```
cell_densities(cell_positions::AbstractVector{T}) where {T<:Number}
```

セルの位置からセル密度を計算します。返されるベクトル `q` は `length(q) = length(cell_positions) - 1` であり、`q[i]` は `i` 番目のセル `(cell_positions[i], cell_positions[i+1])` の密度で、これは `1/(cell_positions[i+1] - cell_positions[i])` で与えられます。

セルの密度ではなく、各ノードでの密度の推定が必要な場合は、[`node_densities`](@ref) を参照してください。
