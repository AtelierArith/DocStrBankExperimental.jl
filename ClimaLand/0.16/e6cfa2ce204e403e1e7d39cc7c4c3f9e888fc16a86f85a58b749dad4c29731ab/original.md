```
initialize_auxiliary(model::AbstractModel, state::NamedTuple)
```

Returns a NamedTuple of auxiliary variables for `model` with the required structure, with values equal to `similar(state)`. This assumes that all  auxiliary variables are defined over the entire domain, and that all auxiliary variables have the same dimension and type. The auxiliary variables NamedTuple can also hold preallocated objects which are not Fields.

If a model has no auxiliary variables, the returned NamedTuple contains only an empty array.

The input `state` is an array-like object, usually a ClimaCore Field or a Vector{FT}.

Adjustments to this - for example because different auxiliary variables have different dimensions - require defining a new method.
