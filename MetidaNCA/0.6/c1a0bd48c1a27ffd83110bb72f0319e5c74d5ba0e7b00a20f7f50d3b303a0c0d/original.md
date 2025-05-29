```
nca(args...; kelauto = true,  elimrange = ElimRange(), dosetime = DoseTime(), kwargs...)

nca(data, time, obs, sort; kelauto = true,  elimrange = ElimRange(), dosetime = DoseTime(), kwargs...)

nca(data, time, obs; kelauto = true,  elimrange = ElimRange(), dosetime = DoseTime(), kwargs...)

nca(time, obs; kelauto = true,  elimrange = ElimRange(), dosetime = DoseTime(), kwargs...)
```

Import data and perform NCA analysis.

Syntax simillar to [`pkimport`](@ref)

Applicable `kwargs` see  [`nca!`](@ref).

See also: [`ElimRange`](@ref), [`DoseTime`](@ref), [`LimitRule`](@ref).
