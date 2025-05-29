```
formal_coefficients(R, name::Symbol)
```

多項式環 `R` の形式的係数を表すオブジェクトを返します。

# 例

```jldoctest
julia> using PolynomialRings

julia> R = @ring! ℤ[x];


julia> c = formal_coefficients(R, :c);



julia> c[1:3]
3-element Array{@ring(ℤ[c[]][x]),1}:
 c[1]
 c[2]
 c[3]

julia> [c()*x^2 + c()*x + c() , c()*x^2 + c()*x + c()]
2-element Array{@ring(ℤ[c[]][x]),1}:
 c[1]*x^2 + c[2]*x + c[3]
 c[4]*x^2 + c[5]*x + c[6]
```
