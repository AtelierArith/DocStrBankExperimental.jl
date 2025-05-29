```
string2F2poly(polynomial::AbstractString) -> Polynomial{F2, :x}
```

多項式の文字列表現をPolynomial{F2, :x}オブジェクトに変換します。

# 例

julia> string2F2poly("x^3 + x + 1") Polynomial(1 + x + x^3)

julia> string2F2poly("x^5") Polynomial(x^5)
