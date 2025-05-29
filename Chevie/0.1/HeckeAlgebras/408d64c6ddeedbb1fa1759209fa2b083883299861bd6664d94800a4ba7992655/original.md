`alt(a::HeckeTElt)`

`a` should be an element of an Iwahori-Hecke algebra `H`. the involution on `H`   defined  by  `x↦  bar(x)`   on  coefficients  and  `Tₛ↦  uₛ,₀uₛ,₁Tₛ`. Essentially it corresponds to tensoring with the sign representation.

```julia-repl
julia> W=coxgroup(:G,2);H=hecke(W,Pol(:q))
hecke(G₂,q)

julia> T=Tbasis(H);h=T(1,2)*T(2,1)
q²T.+(q²-q)T₁+(q-1)T₁₂₁

julia> alt(h)
q⁻²T.+(q⁻²-q⁻³)T₁+(q⁻³-q⁻⁴)T₁₂₁
```
