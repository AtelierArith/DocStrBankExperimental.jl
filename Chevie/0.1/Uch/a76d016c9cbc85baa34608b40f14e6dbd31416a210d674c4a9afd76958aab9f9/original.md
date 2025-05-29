`lusztig_restrict(R,u)`

`u`  should be a unipotent character of a parent Coxeter coset `W` of which `R` is a parabolic subcoset. It represents a unipotent character `γ` of the algebraic  group `𝐆` attached to `W`,  while `R` represents a Levi subgroup `L`. The program returns the Lusztig restriction $*R_𝐋^𝐆(γ)$.

```julia-repl
julia> W=coxgroup(:G,2)
G₂

julia> WF=spets(W)
G₂

julia> T=subspets(WF,Int[],W(1))
G₂₍₎=Φ₁Φ₂

julia> u=dlchar(W,W(1))
[G₂]:<φ₁‚₀>-<φ₁‚₆>-<φ′₁‚₃>+<φ″₁‚₃>

julia> lusztig_restrict(T,u)
[G₂₍₎=Φ₁Φ₂]:4<Id>

julia> T=subspets(WF,Int[],W(2))
G₂₍₎=Φ₁Φ₂

julia> lusztig_restrict(T,u)
[G₂₍₎=Φ₁Φ₂]:0
```
