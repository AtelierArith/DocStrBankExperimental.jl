```
shift(bf::FloatingGTBasisFuncs{T, D, 𝑙, GN, PT, 1}, 
      dl::Union{Vector{Int}, NTuple{D, Int}, LTuple{D}}, op::Function=+) where 
     {T, D, 𝑙, GN, PT} -> 
BasisFunc{T, D, <:Any, GN, PT}
```

Shift (`+` as the default binary operator `op`) the angular momentum (in Cartesian  representation) of the input `FloatingGTBasisFuncs` given `dl` that specifies the change of  each component.
