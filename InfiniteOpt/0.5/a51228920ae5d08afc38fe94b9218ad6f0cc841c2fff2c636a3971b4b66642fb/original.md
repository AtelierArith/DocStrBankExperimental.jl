```
DiscreteMeasureData(pref::GeneralVariableRef,
    coefficients::Vector{<:Real},
    supports::Vector{<:Real};
    [label::Type{<:AbstractSupportLabel} = generate_unique_label(),
    weight_function::Function = [`default_weight`](@ref),
    lower_bound::Real = NaN,
    upper_bound::Real = NaN,
    is_expect::Bool = false]
    )::DiscreteMeasureData
```

Returns a 1-dimensional `DiscreteMeasureData` object that can be utilized to define measures using [`measure`](@ref). This accepts input for a scalar (single) infinite parameter. A description of the other arguments is provided in the documentation for [`DiscreteMeasureData`](@ref). Errors if supports are out bounds or an unequal number of supports and coefficients are given. Note that by default a unique `label` is generated via `generate_unique_label` to ensure the supports can be located in the infinite parameter support storage. Advanced implementations, may choose a different behavior but should do so with caution.

**Example**

```julia-repl
julia> data = DiscreteMeasureData(pref, [0.5, 0.5], [1, 2]);
```
