`class_polynomials(h::HeckeElt)`

returns  the  class  polynomials  of  the  element `h` of the Iwahori-Hecke algebra or coset given by `h.H` with respect to the `T` basis for a set `R` of  representatives  of  minimal  length  in  the  conjugacy classes of the Coxeter group or coset `H.W`. Such minimal length representatives are given by  `classreps(H.W)`. The vector `p` of  these polynomials has the property that  if `X` is the  matrix of the values  of the irreducible characters of `H`  on `T_w` (for `w∈ R`), then the product `X*p` is the list of values of the irreducible characters on `h`.

```julia-repl
julia> W=coxsym(4)
𝔖 ₄

julia> H=hecke(W,Pol(:q))
hecke(𝔖 ₄,q)

julia> h=Tbasis(H,longest(W))
T₁₂₁₃₂₁

julia> p=class_polynomials(h)
5-element Vector{Pol{Int64}}:
 0
 0
 q²
 q³-2q²+q
 q³-q²+q-1
```

The class polynomials were introduced in [Geck-Pfeiffer1993](biblio.htm#GP93).
