```
generate_integral_data(
    prefs::Union{InfiniteOpt.GeneralVariableRef, Vector{InfiniteOpt.GeneralVariableRef}},
    lower_bounds::Union{Real, Vector{<:Real}},
    upper_bounds::Union{Real, Vector{<:Real}},
    method::V; [num_supports::Int = InfiniteOpt.DefaultNumSupports,
    weight_func::Function = InfiniteOpt.default_weight,
    extra_kwargs...]
    )::InfiniteOpt.AbstractMeasureData where {V <: AbstractIntegralMethod}
```

Generate the appropriate concrete realization of `AbstractMeasureData` using `method`. Here `prefs`, `lower_bounds`, and `upper_bounds` will always have a 1 to 1 correspondence when this is called from `integral`. Please refer to the method docstrings for an explanation of each one.

User-defined method extensions should first define a concrete `method` type inheriting from `AbstractUnivariateMethod` or `AbstractMultivariateMethod` as appropriate and then implement extend this method using that type for `method`.
