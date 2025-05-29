```
function randomTTN(sites::Vector{Index{T}}, graph::Graph{Int2},
                   sitenodes::Dict{Int, Int2}, chi::Int, qn::QN = QN()) where T
```

Returns a TTN object, having random elements, from site `Index`s `sites`, the underlyting `graph`, `sitenodes::Dict{Int, Int2}` that maps each site to the corresponding node, initial bond dimension `chi`, and (optional) global QN sector `qn`. The structure is determined by the input `graph` object.

**Note**: This function can be used to generate any loop-free tensor network.

**Note**: For QN conserving TTN, the bond dimension might be off by one or two from `chi`.
