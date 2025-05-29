```
cell_midpoints(cell_positions::AbstractVector{T}) where {T<:Number}
```

セルの位置からセルの中点を計算します。返されるベクトル `x` は `length(x) = length(cell_positions) - 1` であり、`x[i]` は `i` 番目のセル `(cell_positions[i], cell_positions[i+1])` の中点で、`0.5(cell_positions[i] + cell_positions[i+1])` によって与えられます。
