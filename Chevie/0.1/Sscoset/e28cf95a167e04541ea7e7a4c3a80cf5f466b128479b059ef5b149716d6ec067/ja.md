`centralizer(WF::Spets,t::SemisimpleElement{Root1})`  

`WF` は、代数的コセット `𝐆 ⋅σ` を表すコクセターコセットであるべきで、ここで `𝐆` は連結可解群（'W:=Group(WF)' で表される）であり、`σ` は `WF` によって定義された `𝐆` の準中心的自己同型です。要素 `t` は `𝐆` の半単純要素であるべきです。この関数は、`C_𝐆 (tσ)` を記述する拡張反射群を返し、反射群部分は `C_𝐆 ⁰(tσ)` を表し、ダイアグラム自己同型部分は `C_𝐆 (tσ)/C_𝐆 (tσ)⁰` によって `C_𝐆 (tσ)⁰` に誘導されるものです。

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
