```
@flat_coefficients(a, var, [var...])
```

行列 `a` の行列係数を与えられた変数における多項式として見なしたときの *多項式* の係数を返します。

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

`flat_coefficients`, `@expansion`, `expansion`, `@coefficient` および `coefficient`
