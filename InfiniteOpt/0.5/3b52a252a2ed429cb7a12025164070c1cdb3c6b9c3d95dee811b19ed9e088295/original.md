```
@infinite_parameter(model::InfiniteModel, kwargs...)
```

Add *anonymous* infinite parameter to the model `model` described by the keyword arguments `kw_args` and returns the parameter reference.

```julia
@infinite_parameter(model::InfiniteModel, expr, kwargs...)
```

Add an infinite parameter to the model `model` described by the expression `expr`, and the keyword arguments `kw_args`. (Note that in the following the symbol `in`  can be used instead of `∈`) The expression `expr` can be of the form:

  * `paramexpr` creating parameters described by `paramexpr`.
  * `paramexpr ∈ [lb, ub]` creating parameters described by `paramexpr` characterized  by a continuous interval domain with lower bound `lb` and upper bound `ub`.
  * `paramexpr ~ dist` creating parameters described by `paramexpr` characterized  by the `Distributions.jl` distribution object `dist`.
  * `paramexpr ∈ domain` creating parameters described by `paramexpr` characterized  by the `AbstractInfiniteDomain` object `domain`.

The expression `paramexpr` can be of the form:

  * `paramname` creating a scalar parameter of name `paramname`
  * `paramname[...]` or `[...]` creating a container of parameters

The recognized keyword arguments in `kwargs` are the following:

  * `base_name`: Sets the name prefix used to generate parameter names. It corresponds to the parameter name for scalar parameter, otherwise, the parameter names are set to `base_name[...]` for each index `...` of the axes `axes`.
  * `domain`: The `InfiniteDomain` characterizing the parameters see subtypes of           [`AbstractInfiniteDomain`](@ref).
  * `distribution`: Sets the `Distributions.jl` distribution object that   characterizes the parameters (specified instead of a domain).
  * `supports`: Sets the support points for the parameters.
  * `num_supports`: Specifies the number of supports to be automatically generated.                 Note that `supports` takes precedence. Defaults to 0.
  * `derivative_method`: Specify the numerical method to evaluate derivatives that                       are taken with respect to the parameter.
  * `sig_digits`: Specifies the number of significant digits that should be used               in automatic support generation. Defaults to `DefaultSigDigits`.
  * `independent`: Specifies if the each parameter is independent from each other or not. Defaults to false.
  * `container`: Specify the container type. Defaults to `Auto`

**Examples**

```julia-repl
julia> @infinite_parameter(m, x in [0, 1])
x

julia> @infinite_parameter(m, y[i = 1:2] ~ MvNormal(ones(2)), num_supports = 10)
2-element Array{GeneralVariableRef,1}:
 y[1]
 y[2]

julia> z = @infinite_parameter(m, [["a", "b"]], distribution = Normal(),
                               independent = true)
1-dimensional DenseAxisArray{GeneralVariableRef,1,...} with index sets:
    Dimension 1, ["a", "b"]
And data, a 2-element Array{GeneralVariableRef,1}:
 noname[a]
 noname[b]
```
