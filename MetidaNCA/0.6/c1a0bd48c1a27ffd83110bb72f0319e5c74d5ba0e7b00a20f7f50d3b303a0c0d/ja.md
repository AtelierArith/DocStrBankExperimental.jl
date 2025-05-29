```
nca(args...; kelauto = true,  elimrange = ElimRange(), dosetime = DoseTime(), kwargs...)

nca(data, time, obs, sort; kelauto = true,  elimrange = ElimRange(), dosetime = DoseTime(), kwargs...)

nca(data, time, obs; kelauto = true,  elimrange = ElimRange(), dosetime = DoseTime(), kwargs...)

nca(time, obs; kelauto = true,  elimrange = ElimRange(), dosetime = DoseTime(), kwargs...)
```

データをインポートし、NCA分析を実行します。

構文は[`pkimport`](@ref)に似ています。

適用可能な`kwargs`は[`nca!`](@ref)を参照してください。

さらに、[`ElimRange`](@ref)、[`DoseTime`](@ref)、[`LimitRule`](@ref)も参照してください。
