```
applyPulse(spa::AbstractSpinArray, p::Pulse, loc; Δf, b1Map, doHist)
```

`p`を𝐵-効果的に変換し、`spa.M`に適用します。その際、`M, T1, T2, γ`を使用します。

参照: [`blochSim`](@ref), [`freePrec`](@ref).
