```
FunctionalDiscreteMeasureData(pref::GeneralVariableRef,
    coeff_func::Function,
    min_num_supports::Int,
    label::Type{<:AbstractSupportLabel};
    [weight_function::Function = [`default_weight`](@ref),
    lower_bound::Real = NaN,
    upper_bound::Real = NaN,
    is_expect::Bool = false,
    generative_support_info::AbstractGenerativeInfo = NoGenerativeSupports()]
    )::FunctionalDiscreteMeasureData
```

Returns a 1-dimensional `FunctionalDiscreteMeasureData` object that can be utilized to define measures using [`measure`](@ref). This accepts input for a scalar (single) infinite parameter. A description of the other arguments is provided in the documentation for [`FunctionalDiscreteMeasureData`](@ref). Errors if `pref` is not an infinite parameter. Built-in choices for `label` include:

  * `All`: Use all of the supports stored in `pref`
  * `MCSample`: Use Monte Carlo samples associated with `pref`
  * `WeightedSample`: Use weighted Monte Carlo samples associated with `pref`
  * `UniformGrid`: Use uniform grid points associated with `pref`.

**Example**

```julia-repl
julia> data = FunctionalDiscreteMeasureData(pref, my_func, 20, UniformGrid);
```
