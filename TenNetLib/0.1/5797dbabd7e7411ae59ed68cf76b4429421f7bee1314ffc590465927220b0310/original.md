```
function default_randomTTN(sites::Vector{Index{T}}, chi::Int, qn::QN = QN()) where T
```

Returns a TTN object, having random elements, from site `Index`s `sites`, initial bond dimension `chi` and (optional) global QN sector `qn`. The structure is a default hierarchical binary tree graph. Automatically handles situations where the number of sites is not a power of 2.

**Note**: For QN conserving TTN, the bond dimension might be off by one or two from `chi`.
