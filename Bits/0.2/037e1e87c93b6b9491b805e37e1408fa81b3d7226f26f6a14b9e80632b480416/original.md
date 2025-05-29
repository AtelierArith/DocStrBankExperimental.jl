```
weight(x::Real) -> Int
```

Hamming weight of `x` considered as a binary vector. Similarly to `count_ones(x)`, counts the number of `1` in the bit representation of `x`, but not necessarily at the "bare-metal" level; for example `count_ones(big(-1))` errors out, while `weight(big(-1)) == Bits.INF`, i.e. a `BigInt` is considered to be an arbitrary large field of bits with twos complement arithmetic.

# Examples

```jldoctest
julia> weight(123)
6

julia> count(bits(123))
6
```
