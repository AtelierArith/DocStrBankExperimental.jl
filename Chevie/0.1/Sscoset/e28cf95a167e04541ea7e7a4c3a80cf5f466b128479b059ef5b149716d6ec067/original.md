`centralizer(WF::Spets,t::SemisimpleElement{Root1})`  

`WF`  should be  a Coxeter  coset representing  an algebraic coset `𝐆 ⋅σ`, where `𝐆` is a connected reductive group (represented by 'W:=Group(WF)'), and  `σ`  is  a  quasi-central  automorphism  of `𝐆` defined by `WF`. The element  `t` should be a semisimple  element of `𝐆`. The function returns an  extended reflection  group describing  `C_𝐆 (tσ)`, with the reflection group  part representing  `C_𝐆 ⁰(tσ)`, and  the diagram  automorphism part being those induced by `C_𝐆 (tσ)/C_𝐆 (tσ)⁰` on `C_𝐆 (tσ)⁰`.

```julia-repl
julia> WF=rootdatum(:u,6)
u₆

julia> s=ss(Group(WF),[1//4,0,0,0,0,3//4])
SemisimpleElement{Root1}: <ζ₄,1,1,1,1,ζ₄³>

julia> centralizer(WF,s)
B₂Φ₁

julia> centralizer(WF,one(s))
C₃₍₃₂₁₎
```
