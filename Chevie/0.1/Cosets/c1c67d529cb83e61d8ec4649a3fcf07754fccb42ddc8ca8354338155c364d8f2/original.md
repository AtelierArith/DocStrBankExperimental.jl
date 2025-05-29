`twistings(W,I)`

`W`  should be a  complex reflection group.

The  function returns  the list,  up to  `W`-conjugacy, of  subspets of `W` whose  group is `reflection_subgroup(W,I)` –- In  the case of Weyl groups, it  corresponds to  representatives of  the possible  twisted forms  of the reductive subgroup of maximal rank `L` corresponding to `reflection_subgroup(W,I)`.   These  are  classified   by  the  classes  of `N_W(L)/L`.

`W`  could also be a coset `Wϕ`; then the subgroup `L` must be conjugate to `ϕ(L)`  for a  rational form  to exist.  If `wϕ`  normalizes `L`,  then the rational forms are classified by the the `wϕ`-classes of `N_W(L)/L`.

```julia-repl
julia> W=coxgroup(:E,6)
E₆

julia> WF=spets(W,Perm(1,6)*Perm(3,5))
²E₆

julia> twistings(W,2:5)
3-element Vector{Spets{FiniteCoxeterSubGroup{Perm{Int16},Int64}}}:
 E₆₍₂₃₄₅₎=D₄Φ₁²
 E₆₍₂₃₄₅₎=³D₄Φ₃
 E₆₍₂₃₄₅₎=²D₄Φ₁Φ₂


julia> twistings(WF,2:5)
3-element Vector{Spets{FiniteCoxeterSubGroup{Perm{Int16},Int64}}}:
 ²E₆₍₂₃₄₅₎=²D₄₍₁₄₃₂₎Φ₁Φ₂
 ²E₆₍₂₃₄₅₎=³D₄₍₁₄₃₂₎Φ₆
 ²E₆₍₂₃₄₅₎=D₄Φ₂²
```
