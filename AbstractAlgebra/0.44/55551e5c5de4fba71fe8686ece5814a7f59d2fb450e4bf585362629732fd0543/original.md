```
evaluate(E::Expr, vars::Dict)
evaluate(E::Expr, R::MPolyRing)
evaluate(E::Expr, R::PolyRing)
```

Given an rational multivariate expression, evaluate the expression by replacing the occurring symbols using the dictionary `vars` or the variables from the polynomial ring `R`.

# Examples

```jldoctest
julia> evaluate(:((x^2 + 1)//(y + 1//2)), Dict(:x => 1, :y => QQ(2)))
4//5

julia> Qx, (x, y) = QQ[:x, :y];

julia> evaluate(:((x^2 + 1)//(y + 1//2)), Qx)
(x^2 + 1)//(y + 1//2)
```
