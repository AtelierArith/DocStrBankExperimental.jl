```
SemiInfinite{V, VT <: VectorTuple} <: InfOptVariableType
```

A `DataType` to assist in making semi-infinite variables. This can be passed as an  extra argument to `@variable` to make such a variable: 

```julia
@variable(model, var_expr, SemiInfinite(inf_var, parameter_values...), kwargs...)
```

Here `parameter_values` must match the format of the infinite parameter  references associated with the infinite variable `inf_var` and can be comprised  of both real valued supports and/or infinite parameters.

**Fields**

  * `infinite_variable_ref::V`
  * `parameter_values::VT`: The infinite parameters and/or infinite   parameter support values the variable will depend on.
