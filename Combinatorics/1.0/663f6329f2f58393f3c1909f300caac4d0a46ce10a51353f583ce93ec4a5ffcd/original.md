```
multinomial(k...)
```

Compute the multinomial coefficient $\binom{n}{k_1,k_2,...,k_i} = \frac{n!}{k_1!k_2! \cdots k_i!}, n = \sum{k_i}$. Throws an `OverflowError` when the input is too large.

See Also: `binomial`.

# Examples

```jldoctest
julia> # (x+y)^2 = x^2 + 2xy + y^2

julia> multinomial(2, 0)
1

julia> multinomial(1, 1)
2

julia> multinomial(0, 2)
1

julia> multinomial(10, 10, 10, 10)
ERROR: OverflowError: 5550996791340 * 847660528 overflowed for type Int64
Stacktrace:
[...]
```

# External links

  * [Definitions](https://dlmf.nist.gov/26.4.2) on DLMF
  * [Multinomial theorem](https://en.wikipedia.org/wiki/Multinomial_theorem) on Wikipedia
