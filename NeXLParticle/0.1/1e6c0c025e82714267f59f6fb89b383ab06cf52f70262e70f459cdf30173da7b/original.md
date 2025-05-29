```
multiternary(data::DataFrame, cols::AbstractArray{Symbol}, clscol::Union{Symbol, Missing}=missing; palette=TernPalette, norm=1.0)
```

Uses Compose.jl to draw a simple multi-ternary diagram from the `data`, a `DataFrame`. The columns are drawn in the order in `cols` and the vertices labeled with the names of the columns.
