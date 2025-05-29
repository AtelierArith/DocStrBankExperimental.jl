```
continued_fraction(D::Integer, P::Integer=0, Q::Integer=1)
```

Gives the continued fraction of the quadractic number `x = (sqrt(D) + P) / Q`.

More specifically, the iterator `continued_fraction(D, P, Q)` returns 3-Tuples of the form

```
(ai::BigInt, Pi::BigInt, Qi::BigInt),
```

where `ai` is the `i`'th coefficent of the continued fraction, and `Pi / Qi` is the `i`'th convergent of `x`.

# Examples

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
