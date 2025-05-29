```
@NLparameter(model, param == value)
```

Create and return a nonlinear parameter `param` attached to the model `model` with initial value set to `value`. Nonlinear parameters may be used only in nonlinear expressions.

# Example

```jldoctest; setup=:(using JuMP)
model = Model()
@NLparameter(model, x == 10)
value(x)

# output
10.0
```

```
@NLparameter(model, value = param_value)
```

Create and return an anonymous nonlinear parameter `param` attached to the model `model` with initial value set to `param_value`. Nonlinear parameters may be used only in nonlinear expressions.

## Example

```jldoctest; setup=:(using JuMP)
model = Model()
x = @NLparameter(model, value = 10)
value(x)

# output
10.0
```

```
@NLparameter(model, param_collection[...] == value_expr)
```

Create and return a collection of nonlinear parameters `param_collection` attached to the model `model` with initial value set to `value_expr` (may depend on index sets). Uses the same syntax for specifying index sets as [`@variable`](@ref).

## Example

```jldoctest; setup=:(using JuMP)
model = Model()
@NLparameter(model, y[i = 1:10] == 2 * i)
value(y[9])

# output
18.0
```

```
@NLparameter(model, [...] == value_expr)
```

Create and return an anonymous collection of nonlinear parameters attached to the model `model` with initial value set to `value_expr` (may depend on index sets). Uses the same syntax for specifying index sets as [`@variable`](@ref).

## Example

```jldoctest; setup=:(using JuMP)
model = Model()
y = @NLparameter(model, [i = 1:10] == 2 * i)
value(y[9])

# output
18.0
```
