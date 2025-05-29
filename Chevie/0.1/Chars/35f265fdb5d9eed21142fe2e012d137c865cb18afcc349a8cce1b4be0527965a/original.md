`discriminant(W)`

returns  the  discriminant  of  the  complex  reflection  group  `W`,  as a polynomial in the fundamental invariants. The discriminant is the invariant obtained  by  taking  the  product  of  the  linear  forms  describing  the reflecting   hyperplanes  of  `W`,   each  raised  to   the  order  of  the corresponding  reflection. The discriminant  is returned as  a function `f` such  that  the  discriminant  in  the  variables  `a₁,…,aₙ` is obtained by calling `f(a₁,…,aₙ)`. For the moment, this function is implemented only for the exceptional complex reflection groups `G₄` to `G₃₃`.

```julia-repl
julia> W=complex_reflection_group(4);@Mvp x,y

julia> discriminant(W)(x,y)
Mvp{Int64}: x³-y²
```
