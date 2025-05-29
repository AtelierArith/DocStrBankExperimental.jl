```
@finite_parameter(model::InfiniteModel, value, kwargs...)
```

Define and add an anonymous finite parameter to `model` and return its parameter reference. Its value is equal to `value`.

```julia
@finite_parameter(model::InfiniteModel, param_expr == value_expr, kwargs...)
```

Define and add a finite parameter(s) to `model` and return appropriate parameter reference(s). The parameter(s) has/have value(s) indicated by the `value_expr`. The expression `param_expr` can be of the form:

  * `paramname` creating a scalar parameter of name `paramname`
  * `paramname[...]` or `[...]` creating a container of parameters

The expression `value_expr` simply expresses the value of the parameter(s). This is typically a number but could be an array indexed using an index defined in `param_expr`.

The recognized keyword arguments in `kwargs` are the following:

  * `base_name`: Sets the name prefix used to generate parameter names. It corresponds to the parameter name for scalar parameter, otherwise, the parameter names are set to `base_name[...]` for each index `...` of the axes `axes`.
  * `container`: Specify the container type, defaults to `Auto`.

**Examples**

```julia-repl
julia> par = @finite_parameter(model, 2)
noname

julia> vals = [3, 2];

julia> pars = @finite_parameter(model, [i = 1:2] == vals[i], base_name = "par")
2-element Array{ParameterRef,1}:
 par[1]
 par[2]

julia> @finite_parameter(model, par2 == 42)
par2
```
