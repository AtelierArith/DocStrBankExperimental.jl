```
@NLparameter(model, param == value)
```

Create and return a nonlinear parameter `param` attached to the model `model` with initial value set to `value`. Nonlinear parameters may be used only in nonlinear expressions.

## Example

```jldoctest
julia> model = Model();

julia> @NLparameter(model, x == 10)
x == 10.0

julia> value(x)
10.0
```

```
@NLparameter(model, value = param_value)
```

Create and return an anonymous nonlinear parameter `param` attached to the model `model` with initial value set to `param_value`. Nonlinear parameters may be used only in nonlinear expressions.

## Example

```jldoctest
julia> model = Model();

julia> x = @NLparameter(model, value = 10)
parameter[1] == 10.0

julia> value(x)
10.0
```

```
@NLparameter(model, param_collection[...] == value_expr)
```

Create and return a collection of nonlinear parameters `param_collection` attached to the model `model` with initial value set to `value_expr` (may depend on index sets). Uses the same syntax for specifying index sets as [`@variable`](@ref).

## Example

```jldoctest
julia> model = Model();

julia> @NLparameter(model, y[i = 1:3] == 2 * i)
3-element Vector{NonlinearParameter}:
 parameter[1] == 2.0
 parameter[2] == 4.0
 parameter[3] == 6.0

julia> value(y[2])
4.0
```

```
@NLparameter(model, [...] == value_expr)
```

Create and return an anonymous collection of nonlinear parameters attached to the model `model` with initial value set to `value_expr` (may depend on index sets). Uses the same syntax for specifying index sets as [`@variable`](@ref).

!!! compat
    This macro is part of the legacy nonlinear interface. Consider using the new nonlinear interface documented in [Nonlinear Modeling](@ref). In most cases, you can replace a call like `@NLparameter(model, p == value)` with `@variable(model, p in Parameter(value))`.


## Example

```jldoctest
julia> model = Model();

julia> y = @NLparameter(model, [i = 1:3] == 2 * i)
3-element Vector{NonlinearParameter}:
 parameter[1] == 2.0
 parameter[2] == 4.0
 parameter[3] == 6.0

julia> value(y[2])
4.0
```
