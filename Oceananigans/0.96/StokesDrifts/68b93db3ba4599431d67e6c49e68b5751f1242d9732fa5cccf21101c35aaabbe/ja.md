```
UniformStokesDrift(; ∂z_uˢ=zerofunction, ∂z_vˢ=zerofunction, ∂t_uˢ=zerofunction, ∂t_vˢ=zerofunction, parameters=nothing)
```

水平に均一な表面重力波場に対応するストークスドリフト速度場の関数セットを構築します。オプションの `parameters` があります。

`parameters=nothing` の場合、関数 `∂z_uˢ`、`∂z_vˢ`、`∂t_uˢ`、`∂t_vˢ` は `(z, t)` のシグネチャで呼び出すことができなければなりません。`!isnothing(parameters)` の場合、関数は `(z, t, parameters)` のシグネチャで呼び出すことができなければなりません。

ラグランジアン平均運動量の進化を解決するために、ストークスドリフトの水平成分 `uˢ` と `vˢ` の垂直微分と時間微分が必要です。

# 例

表面ストークスドリフト `uˢ(z=0) = 0.005` と減衰スケール `h = 20` に対応する指数関数的に減衰するストークスドリフト：

```jldoctest
using Oceananigans

@inline uniform_stokes_shear(z, t) = 0.005 * exp(z / 20)

stokes_drift = UniformStokesDrift(∂z_uˢ=uniform_stokes_shear)

# output

UniformStokesDrift{Nothing}:
├── ∂z_uˢ: uniform_stokes_shear
├── ∂z_vˢ: zerofunction
├── ∂t_uˢ: zerofunction
└── ∂t_vˢ: zerofunction
```

表面ストークスドリフト `uˢ = 0.005` と減衰スケール `h = 20` に対応する指数関数的に減衰するストークスドリフト、パラメータを使用：

```jldoctest
using Oceananigans

@inline uniform_stokes_shear(z, t, p) = p.uˢ * exp(z / p.h)

stokes_drift_parameters = (uˢ = 0.005, h = 20)
stokes_drift = UniformStokesDrift(∂z_uˢ=uniform_stokes_shear, parameters=stokes_drift_parameters)

# output

UniformStokesDrift with parameters (uˢ=0.005, h=20):
├── ∂z_uˢ: uniform_stokes_shear
├── ∂z_vˢ: zerofunction
├── ∂t_uˢ: zerofunction
└── ∂t_vˢ: zerofunction
```
