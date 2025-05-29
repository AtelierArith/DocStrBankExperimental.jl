```
DoubleLogUpdate(; target_walkers = 1_000, ζ = 0.08, ξ = ζ^2/4) <: ShiftStrategy
```

Strategy for updating the shift according to the log formula with damping parameter `ζ` and `ξ`.

$$
S^{n+1} = S^n -\frac{ζ}{dτ}\ln\left(\frac{\|Ψ\|_1^{n+1}}{\|Ψ\|_1^n}\right)-\frac{ξ}{dτ}\ln\left(\frac{\|Ψ\|_1^{n+1}}{\|Ψ\|_1^\text{target}}\right)
$$

When ξ = ζ^2/4 this corresponds to critical damping with a damping time scale T = 2/ζ.

See [`ShiftStrategy`](@ref), [`ProjectorMonteCarloProblem`](@ref).
