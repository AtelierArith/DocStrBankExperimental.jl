```
@qn <expression>
```

Return the expression, without $ interpolation.

# Examples

```jldoctest
julia> @qn foo(1, x, :y, $z)
:(foo(1, x, :y, $(Expr(:$, :z))))
```
