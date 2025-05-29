```julia
struct Orbit{U<:(AbstractVector), P<:(AbstractVector)} <: AstrodynamicalModels.AstrodynamicalOrbit{U<:(AbstractVector), P<:(AbstractVector)}
```

軌道の完全な表現であり、数値状態とシステムのパラメータを含みます。
