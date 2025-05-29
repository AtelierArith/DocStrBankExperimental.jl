`structure_rational_points_connected_centre(W,q)`

`W`  should be  a Coxeter  group or  a Coxeter  coset representing a finite reductive  group $𝐆 ^F$, and `q` should  be the prime power associated to the  isogeny `F`. The function returns the abelian invariants of the finite abelian group $Z⁰𝐆 ^F$ where `Z⁰𝐆` is the connected center of `𝐆`.

In  the following example one determines the structure of `𝐓(𝔽₃)` where `𝐓` runs over all the maximal tori of `SL`₄.

```julia-repl
julia> l=twistings(rootdatum(:sl,4),Int[])
5-element Vector{Spets{FiniteCoxeterSubGroup{Perm{Int16},Int64}}}:
 A₃₍₎=Φ₁³
 A₃₍₎=Φ₁²Φ₂
 A₃₍₎=Φ₁Φ₂²
 A₃₍₎=Φ₁Φ₃
 A₃₍₎=Φ₂Φ₄

julia> structure_rational_points_connected_centre.(l,3)
5-element Vector{Vector{Int64}}:
 [2, 2, 2]
 [2, 8]
 [4, 8]
 [26]
 [40]
```
