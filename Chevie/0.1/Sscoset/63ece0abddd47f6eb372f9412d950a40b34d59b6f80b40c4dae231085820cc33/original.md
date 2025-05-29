`isisolated(WF::Spets,t::SemisimpleElement{Root1})`

`WF`  should be  a Coxeter  coset representing  an algebraic  coset `𝐆 ⋅σ`, where  `𝐆` is a connected  reductive group (represented by `W=Group(WF)`), and  `σ`  is  a  quasi-central  automorphism  of  `𝐆` defined by `WF`. The element  `t` should be a semisimple element of `𝐆`. The function returns a boolean describing whether `tσ` is isolated, that is whether the Weyl group of `C_𝐆 (tσ)⁰` is not in any proper parabolic subgroup of `W^σ`.

```julia-repl
julia> WF=rootdatum(:u,6)
u₆

julia> l=quasi_isolated_reps(WF)
4-element Vector{SemisimpleElement{Root1}}:
 <1,1,1,1,1,1>
 <ζ₄,ζ₄,ζ₄,ζ₄³,ζ₄³,ζ₄³>
 <ζ₄,ζ₄,1,1,ζ₄³,ζ₄³>
 <ζ₄,1,1,1,1,ζ₄³>

julia> isisolated.(Ref(WF),l)
4-element BitVector:
 1
 1
 1
 0
```
