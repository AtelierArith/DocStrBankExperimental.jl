```
struct ForwardEulerTimeStepper{T} <: AbstractTimeStepper{T}
```

時間ステッピング `∂u/∂t = RHS(u, t)` のための前方オイラータイムステッパー：

```julia
uⁿ⁺¹ = uⁿ + dt * RHS(uⁿ, tⁿ)
```
