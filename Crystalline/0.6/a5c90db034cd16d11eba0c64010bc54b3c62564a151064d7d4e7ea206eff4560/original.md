```
reduce_ops(ops::AbstractVector{SymOperation{D}},
           cntr::Char,
           conv_or_prim::Bool=true,
           modw::Bool=true) --> Vector{SymOperation{D}}
```

Reduce the operations `ops`, removing operations that are identical in the primitive basis associated with the centering `cntr`. 

If `conv_or_prim = false`, the reduced operations are returned in the primitive basis associated with `cntr`; otherwise, in the conventional. If `modw = true`, the comparison in the primitive basis is done modulo unit primitive lattice vectors; otherwise not. A final argument of type `::Val{P}` can be specified to indicate a subperiodic group of periodicity dimension `P`, different from the spatial embedding dimension `D`.
