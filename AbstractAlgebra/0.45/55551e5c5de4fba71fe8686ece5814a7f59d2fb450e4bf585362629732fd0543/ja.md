```
evaluate(E::Expr, vars::Dict)
evaluate(E::Expr, R::MPolyRing)
evaluate(E::Expr, R::PolyRing)
```

与えられた有理多変数式に対して、辞書 `vars` または多項式環 `R` からの変数を使用して出現する記号を置き換えることによって式を評価します。

# 例

```jldoctest
julia> evaluate(:((x^2 + 1)//(y + 1//2)), Dict(:x => 1, :y => QQ(2)))
4//5

julia> Qx, (x, y) = QQ[:x, :y];

julia> evaluate(:((x^2 + 1)//(y + 1//2)), Qx)
(x^2 + 1)//(y + 1//2)
```
