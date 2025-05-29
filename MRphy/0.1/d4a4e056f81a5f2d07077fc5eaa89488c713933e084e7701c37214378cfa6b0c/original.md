```
applyPulse(spa::AbstractSpinArray, p::Pulse, loc; Δf, b1Map, doHist)
```

Turn `p` into 𝐵-effective and apply it on `spa.M`, using its own `M, T1, T2, γ`.

See also: [`blochSim`](@ref), [`freePrec`](@ref).
