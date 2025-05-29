```
add_to_expression!(expression, terms...)
```

Updates `expression` in-place to `expression + (*)(terms...)`.

This is typically much more efficient than `expression += (*)(terms...)` because it avoids the temorary allocation of the right-hand side term.

For example, `add_to_expression!(expression, a, b)` produces the same result as `expression += a*b`, and `add_to_expression!(expression, a)` produces the same result as `expression += a`.

## When to implement

Only a few methods are defined, mostly for internal use, and only for the cases when:

1. they can be implemented efficiently
2. `expression` is capable of storing the result. For example, `add_to_expression!(::AffExpr, ::GenericVariableRef, ::GenericVariableRef)` is not defined because a `GenericAffExpr` cannot store the product of two variables.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x)
x

julia> expr = 2 + x
x + 2

julia> add_to_expression!(expr, 3, x)
4 x + 2

julia> expr
4 x + 2
```

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2])
2-element Vector{VariableRef}:
 x[1]
 x[2]

julia> @expression(model, ex1, sum(x))
x[1] + x[2]

julia> @expression(model, ex2, 2 * sum(x))
2 x[1] + 2 x[2]

julia> add_to_expression!(ex1, ex2)
3 x[1] + 3 x[2]

julia> ex1
3 x[1] + 3 x[2]

julia> ex2
2 x[1] + 2 x[2]
```
