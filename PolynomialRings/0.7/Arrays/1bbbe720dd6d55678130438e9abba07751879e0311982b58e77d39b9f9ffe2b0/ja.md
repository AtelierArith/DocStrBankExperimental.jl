```
flat_coefficients(a, symbol, [symbol...])
```

与えられた変数において多項式と見なされるとき、`a`の*行列*係数の*多項式*係数を返します。

# 例

```jldoctest
julia> using PolynomialRings

julia> R = @ring! ℤ[x,y];

julia> collect(flat_coefficients([x^3 + y^2; y^5], :y))
3-element Array{@ring(ℤ[x]),1}:
 1
 x^3
 1

julia> collect(flat_coefficients([x^3 + y^2, y^5], :x, :y))
3-element Array{BigInt,1}:
 1
 1
 1
```

# 参照

`@expandcoefficients`, `@expansion`, `expansion`, `@coefficient` および `coefficient`
