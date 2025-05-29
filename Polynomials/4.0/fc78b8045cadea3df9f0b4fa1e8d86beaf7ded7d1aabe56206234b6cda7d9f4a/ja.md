```
gcd(a::AbstractPolynomial, b::AbstractPolynomial; atol::Real=0, rtol::Real=Base.rtoldefault)
```

2つの多項式の最大公約数を再帰的に求めるには、[ユークリッドのアルゴリズム](http://en.wikipedia.org/wiki/Polynomial_greatest_common_divisor#Euclid.27s_algorithm)を使用します。

# 例

```jldoctest
julia> using Polynomials

julia> gcd(fromroots([1, 1, 2]), fromroots([1, 2, 3]))
Polynomial(4.0 - 6.0*x + 2.0*x^2)
```
