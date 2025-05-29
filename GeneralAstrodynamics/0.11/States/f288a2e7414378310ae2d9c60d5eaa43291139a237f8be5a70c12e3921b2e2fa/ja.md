```julia
struct R2BPParameters{F, MU, LU, TU, AU, B} <: GeneralAstrodynamics.States.ParameterVector{F, MU, LU, TU, AU, 1, (:μ,), B}
```

制限された二体問題に必要なすべてのパラメータ。
