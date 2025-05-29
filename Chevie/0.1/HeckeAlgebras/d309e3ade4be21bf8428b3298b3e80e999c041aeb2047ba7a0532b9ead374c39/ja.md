`factorized_schur_element(H,phi)`

は、パラメータ `phi` の Hecke 代数 `H` の irreducible character の因子化された `schur_element` (詳細は `factorized_schur_elements` を参照) を返します (詳細は `charinfo(W).charparams` を参照)。

```julia-repl
julia> W=complex_reflection_group(4)
G₄

julia> @Mvp x,y; H=hecke(W,[[1,x,y]])
hecke(G₄,Vector{Mvp{Int64, Int64}}[[1, x, y]])

julia> factorized_schur_element(H,[[2,5]])
-x⁻¹y(xy+1)(x-1)Φ₆(xy⁻¹)(y-1)
```
