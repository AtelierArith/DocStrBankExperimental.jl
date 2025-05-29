```
Deriv{V, P} <: InfOptVariableType
```

A `DataType` to assist in making derivative variables. This can be passed as an  extra argument to `@variable` to make such a variable: 

```julia
@variable(model, var_expr, Deriv(inf_var, inf_par), kwargs...)
```

Here `inf_var` is the infinite variable that is being operated on and `inf_par`  is the infinite parameter that the derivative is defined with respect to.

**Fields**

  * `argument::V`: The infinite variable being operated on.
  * `operator_parameter::P:` The infinite parameter that determines the derivative.
