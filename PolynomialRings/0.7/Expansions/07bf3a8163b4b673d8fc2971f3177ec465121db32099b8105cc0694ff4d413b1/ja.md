```
expansion_terms(f, symbol, [symbol...])
```

与えられた変数において多項式として展開されたときの `f` の項を返します。

# 例

```jldoctest
julia> using PolynomialRings

julia> R = @ring! ℤ[x,y];

julia> collect(expansion_terms(x^3 + y^2 + 1, :y))
2-element Array{@ring(ℤ[x][y]),1}:
 x^3 + 1
 y^2

julia> collect(expansion_terms(x^3 + y^2 + 1, :x, :y))
3-element Array{@ring(ℤ[x,y]),1}:
 1
 y^2
 x^3
```

# 参照

`@expandcoefficients`, `@expansion`, `expansion`, `@coefficient` および `coefficient`
