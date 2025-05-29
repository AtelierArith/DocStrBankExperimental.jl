```
Infinite{VT <: VectorTuple} <: InfOptVariableType
```

A `DataType` to assist in making infinite variables. This can be passed as an  extra argument to `@variable` to make an infinite variable: 

```julia
@variable(model, var_expr, Infinite(parameter_refs...), args..., kwargs...)
```

Here `parameter_refs` can be a single parameter reference, a single parameter  array with parameters defined in the same macro call, or multiple arguments where  each argument is either of the first two options listed.

**Fields**

  * `parameter_refs::VT`: The infinite parameters the variable will depend on.
