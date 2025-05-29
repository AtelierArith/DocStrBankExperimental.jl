`factorized_schur_element(H,phi)`

returns  the factorized `schur_element`  (see `factorized_schur_elements`) of the  Hecke algebra  `H` for  the irreducible  character of `H` of parameter `phi` (see `charinfo(W).charparams`)

```julia-repl
julia> W=complex_reflection_group(4)
G₄

julia> @Mvp x,y; H=hecke(W,[[1,x,y]])
hecke(G₄,Vector{Mvp{Int64, Int64}}[[1, x, y]])

julia> factorized_schur_element(H,[[2,5]])
-x⁻¹y(xy+1)(x-1)Φ₆(xy⁻¹)(y-1)
```
