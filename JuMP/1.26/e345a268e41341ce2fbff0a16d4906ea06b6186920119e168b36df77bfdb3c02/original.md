```
flatten!(expr::GenericNonlinearExpr)
```

Flatten a nonlinear expression in-place by lifting nested `+` and `*` nodes into a single n-ary operation.

## Motivation

Nonlinear expressions created using operator overloading can be deeply nested and unbalanced. For example, `prod(x for i in 1:4)` creates `*(x, *(x, *(x, x)))` instead of the more preferable `*(x, x, x, x)`.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x)
x

julia> y = prod(x for i in 1:4)
((x²) * x) * x

julia> flatten!(y)
(x²) * x * x

julia> flatten!(sin(prod(x for i in 1:4)))
sin((x²) * x * x)
```
