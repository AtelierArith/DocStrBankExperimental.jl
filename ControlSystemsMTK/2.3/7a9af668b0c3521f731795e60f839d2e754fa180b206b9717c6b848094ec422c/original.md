```
RobustAndOptimalControl.named_ss(sys::ModelingToolkit.AbstractTimeDependentSystem, inputs, outputs; descriptor=true, kwargs...)
```

Convert an `ODESystem` to a `NamedStateSpace` using linearization. `inputs, outputs` are vectors of variables determining the inputs and outputs respectively. See docstring of `ModelingToolkit.linearize` for more info on `kwargs`.

If `descriptor = true` (default), this method automatically converts systems that MTK has failed to produce a proper form for into a proper linear statespace system using the method described here: https://juliacontrol.github.io/ControlSystemsMTK.jl/dev/#Internals:-Transformation-of-non-proper-models-to-proper-statespace-form If `descriptor = false`, the system is instead converted to a statespace realization using `sys[:,uinds] + sys[:,duinds]*tf('s')`, which tends to result in a larger realization on which the user may want to call `minreal(sys, tol)` with a carefully selected tolerance.

See also [`ModelingToolkit.linearize`](@ref) which is the lower-level function called internally. The functions [`get_named_sensitivity`](@ref), [`get_named_comp_sensitivity`](@ref), [`get_named_looptransfer`](@ref) similarily provide convenient ways to compute sensitivity functions while retaining signal names in the same way as `named_ss`. The corresponding lower-level functions `get_sensitivity`, `get_comp_sensitivity` and `get_looptransfer` are available in ModelingToolkitStandardLibrary.Blocks and are documented in [MTKstdlib: Linear analysis](https://docs.sciml.ai/ModelingToolkitStandardLibrary/stable/API/linear_analysis/).
