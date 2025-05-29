`isisolated(WF::Spets,t::SemisimpleElement{Root1})`

`WF` は、代数的コセット `𝐆 ⋅σ` を表すコクセターコセットであるべきで、ここで `𝐆` は連結冪根群（`W=Group(WF)` で表される）であり、`σ` は `WF` によって定義された `𝐆` の準中心自己同型です。要素 `t` は `𝐆` の半単純要素であるべきです。この関数は、`tσ` が孤立しているかどうか、すなわち `C_𝐆 (tσ)⁰` のワイル群が `W^σ` の任意の適切な放物群に含まれていないかどうかを示すブール値を返します。

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
