```
function updateH!(sysenv::StateEnvs{ProjCouplingModel_MPS}, H::CouplingModel, Ms::Vector{MPS};
                  weight::Float64, recalcEnv::Bool = true)
```

`sysenv::StateEnvs`内のハミルトニアン`H`を更新します。`recalcEnv = false`はサポートされていません。

  * `weight::Union{Nothing, Float64} = nothing`。
