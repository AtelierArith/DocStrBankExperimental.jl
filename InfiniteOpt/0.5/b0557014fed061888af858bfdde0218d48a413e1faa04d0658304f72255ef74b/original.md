```
DiscreteMeasureData(prefs::AbstractArray{GeneralVariableRef},
    coefficients::Vector{<:Real},
    supports::Vector{<:AbstractArray{<:Real}};
    label::Type{<:AbstractSupportLabel} = generate_unique_label(),
    weight_function::Function = [`default_weight`](@ref),
    lower_bounds::AbstractArray{<:Real} = [NaN...],
    upper_bounds::AbstractArray{<:Real} = [NaN...],
    is_expect::Bool = false
    )::DiscreteMeasureData
```

Returns a `DiscreteMeasureData` object that can be utilized to define measures using [`measure`](@ref). This accepts input for an array (multi) parameter. The inner arrays in the supports vector need to match the formatting of the array used for `parameter_refs`. A description of the other arguments is provided in the documentation for [`DiscreteMeasureData`](@ref). Errors if supports are out bounds, an unequal number of supports and coefficients are given, the array formats do not match, or if mixed infinite parameter types are given. Note that by default a unique `label` is generated via `generate_unique_label` to ensure the supports can be located in the infinite parameter support storage. Advanced implementations, may choose a different behavior but should do so with caution.

**Example**

```julia-repl
julia> data = DiscreteMeasureData(prefs, [0.5, 0.5], [[1, 1], [2, 2]]);
```
