```
DoubleLogUpdate(; target_walkers = 1_000, ζ = 0.08, ξ = ζ^2/4) <: ShiftStrategy
```

シフトを更新するための戦略で、減衰パラメータ `ζ` と `ξ` に基づいています。

$$
S^{n+1} = S^n -\frac{ζ}{dτ}\ln\left(\frac{\|Ψ\|_1^{n+1}}{\|Ψ\|_1^n}\right)-\frac{ξ}{dτ}\ln\left(\frac{\|Ψ\|_1^{n+1}}{\|Ψ\|_1^\text{target}}\right)
$$

ξ = ζ^2/4 のとき、これは臨界減衰に対応し、減衰時間スケール T = 2/ζ になります。

See [`ShiftStrategy`](@ref), [`ProjectorMonteCarloProblem`](@ref).
