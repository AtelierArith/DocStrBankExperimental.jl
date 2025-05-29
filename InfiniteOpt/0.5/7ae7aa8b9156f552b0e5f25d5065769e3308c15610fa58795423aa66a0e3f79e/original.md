```
FunctionalDiscreteMeasureData(prefs::AbstractArray{GeneralVariableRef},
    coeff_func::Function,
    min_num_supports::Int,
    label::Type{<:AbstractSupportLabel};
    [weight_function::Function = [`default_weight`](@ref),
    lower_bounds::AbstractArray{<:Real} = [NaN...],
    upper_bounds::AbstractArray{<:Real} = [NaN...],
    is_expect::Bool = false]
    )::FunctionalDiscreteMeasureData
```

Returns a multi-dimensional `FunctionalDiscreteMeasureData` object that can be utilized to define measures using [`measure`](@ref). This accepts input for an array of infinite parameters. A description of the other arguments is provided in the documentation for [`FunctionalDiscreteMeasureData`](@ref). Errors if `prefs` are not infinite parameters or if the mixed parameter types are provided. Built-in choices for `label` include:

  * `All`: Use all of the supports stored in `prefs`
  * `MCSample`: Use Monte Carlo samples associated with `prefs`
  * `WeightedSample`: Use weighted Monte Carlo samples associated with `prefs`
  * `UniformGrid`: Use uniform grid points associated with `prefs`.

**Example**

```julia-repl
julia> data = FunctionalDiscreteMeasureData(prefs, my_func, 20, MCSample);
```
