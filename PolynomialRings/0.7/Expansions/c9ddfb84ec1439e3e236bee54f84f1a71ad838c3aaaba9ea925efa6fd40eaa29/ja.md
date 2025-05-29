```
expandcoefficients(f, symbol, [symbol...])
```

与えられた変数に対して多項式として展開されたときの `f` の係数を返します。

# 例

```jldoctest
julia> using PolynomialRings

julia> R = @ring! ℤ[x,y];

julia> collect(expandcoefficients(x^3 + y^2, :y))
2-element Array{@ring(ℤ[x]),1}:
 x^3
 1

julia> collect(expandcoefficients(x^3 + y^2, :x, :y))
2-element Array{BigInt,1}:
 1
 1
```

# 参照

`@expandcoefficients`, `@expansion`, `expansion`, `@coefficient` および `coefficient`
