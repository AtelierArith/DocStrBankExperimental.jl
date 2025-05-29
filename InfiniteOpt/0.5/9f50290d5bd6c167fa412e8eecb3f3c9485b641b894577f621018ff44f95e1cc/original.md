```
InfOptSensitivityReport
```

A wrapper `DataType` for `JuMP.SensitivityReport`s in `InfiniteOpt`.  These are generated based on the optimizer model and should be made via the use of  [`lp_sensitivity_report`](@ref JuMP.lp_sensitivity_report(::InfiniteModel)). Once  made these can be indexed to get the sensitivies with respect to variables and/or  constraints. The indexing syntax for these is: 

```julia
report[ref::[GeneralVariableRef/InfOptConstraintRef]; 
       [label::Type{<:AbstractSupportLabel} = PublicLabel,
       ndarray::Bool = false, kwargs...]]
```

This is enabled in user-defined optimizer model extensions by appropriately  extending [`optimizer_model_variable`](@ref) and [`optimizer_model_constraint`](@ref).

**Fields**

  * `opt_report::JuMP.SensitivityReport`: The LP sensitivity captured from the optimizer model.
