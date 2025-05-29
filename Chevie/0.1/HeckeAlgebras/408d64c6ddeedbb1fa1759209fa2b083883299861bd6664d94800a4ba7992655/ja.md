`alt(a::HeckeTElt)`

`a` は Iwahori-Hecke 代数 `H` の要素である必要があります。`H` における反転は、係数に対して `x↦ bar(x)` によって定義され、`Tₛ↦ uₛ,₀uₛ,₁Tₛ` です。本質的には、符号表現とのテンソル積に対応します。

```julia-repl
julia> W=coxgroup(:G,2);H=hecke(W,Pol(:q))
hecke(G₂,q)

julia> T=Tbasis(H);h=T(1,2)*T(2,1)
q²T.+(q²-q)T₁+(q-1)T₁₂₁

julia> alt(h)
q⁻²T.+(q⁻²-q⁻³)T₁+(q⁻³-q⁻⁴)T₁₂₁
```
