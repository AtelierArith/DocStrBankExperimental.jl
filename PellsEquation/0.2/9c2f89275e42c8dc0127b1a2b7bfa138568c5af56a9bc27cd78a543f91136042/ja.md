```
continued_fraction(D::Integer, P::Integer=0, Q::Integer=1)
```

整数 `D` の連分数を返します。具体的には、数 `x = (sqrt(D) + P) / Q` の連分数です。

より具体的には、イテレータ `continued_fraction(D, P, Q)` は次の形式の3タプルを返します。

```
(ai::BigInt, Pi::BigInt, Qi::BigInt),
```

ここで `ai` は連分数の `i` 番目の係数であり、`Pi / Qi` は `x` の `i` 番目の収束です。

# 例

```jldoctest
julia> collect(Iterators.take(continued_fraction(14, -9, -13), 12))
12-element Vector{Tuple{Int64, BigInt, BigInt}}:
 (0, 0, 1)
 (2, 1, 2)
 (2, 2, 5)
 (8, 17, 42)
 (1, 19, 47)
 (1, 36, 89)
 (18, 667, 1649)
 (1, 703, 1738)
 (12, 9103, 22505)
 (1, 9806, 24243)
 (18, 185611, 458879)
 (1, 195417, 483122)

julia> 667//1649 == 0 + (1//(2 + 1//(2 + 1//(8 + 1//(1 + 1//(1 + 1//18))))))
true

julia> (sqrt(14) - 9) / -13 ≈ 195417 / 483122
true
```
