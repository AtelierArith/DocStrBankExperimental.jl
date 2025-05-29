```
@variable(model, expr, args..., kw_args...)
```

Add a variable to the model `model` described by the expression `expr`, the positional arguments `args` and the keyword arguments `kw_args`.

## Anonymous and named variables

`expr` must be one of the forms:

  * Omitted, like `@variable(model)`, which creates an anonymous variable
  * A single symbol like `@variable(model, x)`
  * A container expression like `@variable(model, x[i=1:3])`
  * An anoymous container expression like `@variable(model, [i=1:3])`

## Bounds

In addition, the expression can have bounds, such as:

  * `@variable(model, x >= 0)`
  * `@variable(model, x <= 0)`
  * `@variable(model, x == 0)`
  * `@variable(model, 0 <= x <= 1)`

and bounds can depend on the indices of the container expressions:

  * `@variable(model, -i <= x[i=1:3] <= i)`

## Sets

You can explicitly specify the set to which the variable belongs:

  * `@variable(model, x in MOI.Interval(0.0, 1.0))`

For more information on this syntax, read [Variables constrained on creation](@ref).

## Positional arguments

The recognized positional arguments in `args` are the following:

  * `Bin`: restricts the variable to the [`MOI.ZeroOne`](@ref) set, that is, `{0, 1}`. For example, `@variable(model, x, Bin)`. Note: you cannot use `@variable(model, Bin)`, use the `binary` keyword instead.
  * `Int`: restricts the variable to the set of integers, that is, ..., -2, -1,  0, 1, 2, ... For example, `@variable(model, x, Int)`. Note: you cannot use  `@variable(model, Int)`, use the `integer` keyword instead.
  * `Symmetric`: Only available when creating a square matrix of variables, i.e., when `expr` is of the form `varname[1:n,1:n]` or `varname[i=1:n,j=1:n]`, it creates a symmetric matrix of variables.
  * `PSD`: A restrictive extension to `Symmetric` which constraints a square matrix of variables to `Symmetric` and constrains to be positive semidefinite.

## Keyword arguments

Four keyword arguments are useful in all cases:

  * `base_name`: Sets the name prefix used to generate variable names. It corresponds to the variable name for scalar variable, otherwise, the variable names are set to `base_name[...]` for each index `...` of the axes `axes`.
  * `start::Float64`: specify the value passed to `set_start_value` for each variable
  * `container`: specify the container type. See [Forcing the container type](@ref variable_forcing) for more information.
  * `set_string_name::Bool = true`: control whether to set the [`MOI.VariableName`](@ref) attribute. Passing `set_string_name = false` can improve performance.

Other keyword arguments are needed to disambiguate sitations with anonymous variables:

  * `lower_bound::Float64`: an alternative to `x >= lb`, sets the value of the variable lower bound.
  * `upper_bound::Float64`: an alternative to `x <= ub`, sets the value of the variable upper bound.
  * `binary::Bool`: an alternative to passing `Bin`, sets whether the variable is binary or not.
  * `integer::Bool`: an alternative to passing `Int`, sets whether the variable is integer or not.
  * `set::MOI.AbstractSet`: an alternative to using `x in set`
  * `variable_type`: used by JuMP extensions. See [Extend `@variable`](@ref extend_variable_macro) for more information.

## Examples

The following are equivalent ways of creating a variable `x` of name `x` with lower bound 0:

```julia
model = Model()
@variable(model, x >= 0)
@variable(model, x, lower_bound = 0)
x = @variable(model, base_name = "x", lower_bound = 0)
```

Other examples:

```julia
model = Model()
@variable(model, x[i=1:3] <= i, Int, start = sqrt(i), lower_bound = -i)
@variable(model, y[i=1:3], container = DenseAxisArray, set = MOI.ZeroOne())
@variable(model, z[i=1:3], set_string_name = false)
```
