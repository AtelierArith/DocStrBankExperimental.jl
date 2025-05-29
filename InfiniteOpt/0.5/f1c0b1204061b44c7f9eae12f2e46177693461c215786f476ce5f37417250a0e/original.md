```
@parameter_function(model::InfiniteModel, func_expr, kwargs...)
```

Add an *anonymous* parameter function to the model `model` described by the keyword arguments `kw_args` and returns the object reference.

```julia
@parameter_function(model::InfiniteModel, var_expr == func_expr, kwargs...)
```

Add a parameter function to `model` described by the expression `var_expr`, the function expression `func_expr`, and the keyword arguments `kwargs`. The  expression `var_expr` is used to define the parameter function references of the  form `varname[...]` where the indexing matches the container syntax of other  macros.

The expression `func_expr` determines the concrete Julia function that defines the  behavior of parameter function and also specifies the infinite parameters it  depends on. The accepted forms are:

  * `func(params...)`: where `func` is the function that takes supports of the  infinite parameters `params` as input and outputs a scalar value.
  * `(params...) -> my_func_expr`: where `params` are the infinite parameters and  `my_func_expr` is the source code of the anonymous function.

The recognized keyword arguments in `kwargs` are the following:

  * `base_name`: Sets the name prefix used to generate object names. It corresponds to the object name for scalar parameter function, otherwise, the object names are set to `base_name[...]` for each index `...` of the axes `axes`.
  * `container`: Specify the container type. Defaults to `:Auto`.

**Examples**

```julia-repl
julia> @parameter_function(model, sin(t))
sin(t)

julia> func_vect = [sin, cos];

julia> @parameter_function(model, [i = 1:2] == func_vect[i](t))
2-element Array{GeneralVariableRef,1}:
 sin(t)
 cos(t)

julia> f(t_val, x_vals) = t_val + sum(x_vals)
f (generic function with 1 method)

julia> @parameter_function(model, pf == f(t, x))
pf(t, x)

julia> g(t_val, a; b = 0) = t_val + a + b
g (generic function with 1 method)

julia> @parameter_function(model, pf2[i = 1:2] == t -> g(t, i, b = 2 * i ))
2-element Array{GeneralVariableRef,1}:
 pf2[1](t)
 pf2[2](t)
```
