```
LogUpdate(ζ = 0.08) <: ShiftStrategy
```

Strategy for updating the shift according to the log formula with damping parameter `ζ`.

$$
S^{n+1} = S^n -\frac{ζ}{dτ}\ln\left(\frac{\|Ψ\|_1^{n+1}}{\|Ψ\|_1^n}\right)
$$

See [`ShiftStrategy`](@ref), [`ProjectorMonteCarloProblem`](@ref).
