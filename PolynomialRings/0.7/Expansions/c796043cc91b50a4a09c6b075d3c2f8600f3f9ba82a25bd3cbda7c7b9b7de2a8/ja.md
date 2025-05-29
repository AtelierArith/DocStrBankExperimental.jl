```
expansion(f, symbol, [symbol...])
```

fをその構成要素に分解する(monomial, coefficient)タプルのコレクションを返します。

REPLでは、より使いやすいバージョンの`@expansion`を使用することをお勧めします。

# 例

```jldoctest
julia> using PolynomialRings

julia> R = @ring! ℤ[x,y];

julia> collect(expansion(x^3 + y^2, :y))
2-element Array{(Term over @ring(ℤ[x]) in @degrevlex(y)),1}:
 x^3
 y^2

julia> collect(expansion(x^3 + y^2, :x, :y))
2-element Array{(Term over BigInt in @degrevlex(x > y)),1}:
 y^2
 x^3
```

# 参照

`@expansion(...)`、`@coefficient`および`coefficient`
