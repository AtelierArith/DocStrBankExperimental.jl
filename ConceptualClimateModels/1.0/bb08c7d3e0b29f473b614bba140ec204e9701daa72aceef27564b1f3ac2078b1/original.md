```
processes_to_coupledodes(processes [, default]; kw...)
```

Convert a given `Vector` of processes to a `DynamicalSystem`, in particular `CoupledODEs`. All processes represent symbolic equations managed by ModelingToolkit.jl. `default` is a vector for default processes that "process-less" variables introduced in `processes` will obtain. Use [`processes_to_mtkmodel`](@ref) to obtain the MTK model before it is structurally simplified and converted to a `DynamicalSystem`. See also [`processes_to_mtkmodel`](@ref) for more details on what `processes` is, or see the online [Tutorial](@ref).

## Keyword arguments

  * `diffeq`: options passed to DifferentialEquations.jl ODE solving when constructing the `CoupledODEs`.
  * `inplace`: whether the dynamical system will be in place or not. Defaults to `true` if the system dimension is ≤ 5.
  * `split = false`: whether to split parameters as per ModelingToolkit.jl. Note the default is not ModelingToolkit's default, i.e., no splitting occurs. This accelerates parameter access, assuming all parameters are of the same type.
  * `kw...`: all other keywords are propagated to `processes_to_mtkmodel`.
