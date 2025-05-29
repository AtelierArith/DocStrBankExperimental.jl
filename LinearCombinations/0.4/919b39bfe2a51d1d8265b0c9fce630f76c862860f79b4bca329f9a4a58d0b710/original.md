```
is_domain(::Type{R}) where R -> Bool
```

Return `true` if the ring `R` is known to be integral domain and `false` otherwise. An integral domain is a commutative ring without zero divisors.

By default, `is_domain` returns `true` only for subtypes of `Real` and `Complex`. If `is_domain(R) == true`, then sometimes more efficient algorithms can be chosen.

See also [`has_char2`](@ref).
