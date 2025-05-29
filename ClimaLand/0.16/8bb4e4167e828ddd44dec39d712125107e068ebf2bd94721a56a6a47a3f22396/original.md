```
initialize_prognostic(model::AbstractModel, state::NamedTuple)
```

Returns a FieldVector of prognostic variables for `model` with the required structure, with values equal to `similar(state)`. This assumes that all prognostic variables are defined over the entire domain, and that all prognostic variables have the same dimension and type.

If a model has no prognostic variables, the returned FieldVector contains only an empty array.

The input `state` is an array-like object, usually a ClimaCore Field or a Vector{FT}.

Adjustments to this - for example because different prognostic variables have different dimensions - require defining a new method.
