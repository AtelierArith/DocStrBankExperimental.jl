```julia
struct CR3BPParameters{F, MU, LU, TU, AU, B} <: GeneralAstrodynamics.States.ParameterVector{F, MU, LU, TU, AU, 1, (:μ,), B}
```

円形制限三体問題に必要なすべてのパラメータ。
