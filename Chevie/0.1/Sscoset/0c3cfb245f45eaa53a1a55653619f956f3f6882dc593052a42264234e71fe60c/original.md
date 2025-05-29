`quasi_isolated_reps(WF::Spets,p=0)`

`WF`  should be  a Coxeter  coset representing  an algebraic  coset `𝐆 ⋅σ`, where  `𝐆` is a connected  reductive group (represented by `W=Group(WF)`), and  `σ`  is  a  quasi-central  automorphism  of  `𝐆` defined by `WF`. The function returns a list of semisimple elements of `𝐆` such that `tσ`, when `t`  runs over this  list, are representatives  of the conjugacy classes of quasi-isolated quasisemisimple elements of `𝐆 ⋅σ` (an element `tσ∈ 𝐓 ⋅σ` is quasi-isolated  if  the  Weyl  group  of  `C_𝐆  (tσ)`  is not in any proper parabolic  subgroup of `W^σ`). If a second  argument `p` is given, it lists only those representatives which exist in characteristic `p`.

```julia-repl
julia> WF=rootdatum("2E6sc")
²E₆sc

julia> quasi_isolated_reps(WF)
5-element Vector{SemisimpleElement{Root1}}:
 <1,1,1,1,1,1>
 <1,-1,ζ₄,1,ζ₄,1>
 <1,1,1,-1,1,1>
 <1,ζ₃²,1,ζ₃,1,1>
 <1,ζ₄³,1,-1,1,1>

julia> quasi_isolated_reps(WF,2)
2-element Vector{SemisimpleElement{Root1}}:
 <1,1,1,1,1,1>
 <1,ζ₃²,1,ζ₃,1,1>

julia> quasi_isolated_reps(WF,3)
4-element Vector{SemisimpleElement{Root1}}:
 <1,1,1,1,1,1>
 <1,-1,ζ₄,1,ζ₄,1>
 <1,1,1,-1,1,1>
 <1,ζ₄³,1,-1,1,1>
```
