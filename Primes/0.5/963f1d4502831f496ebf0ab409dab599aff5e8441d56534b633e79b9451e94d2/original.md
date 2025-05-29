```
divisors(n::Integer) -> Vector
```

Return a vector with the positive divisors of `n`.

For a nonzero integer `n` with prime factorization `n = p₁^k₁ ⋯ pₘ^kₘ`, `divisors(n)` returns a vector of length (k₁ + 1)⋯(kₘ + 1) containing the divisors of `n` in lexicographic (rather than numerical) order.

`divisors(-n)` is equivalent to `divisors(n)`.

For convenience, `divisors(0)` returns `[]`.

# Example

```jldoctest; filter = r"(\s+#.*)?"
julia> divisors(60)
12-element Vector{Int64}:
  1         # 1
  2         # 2
  4         # 2 * 2
  3         # 3
  6         # 3 * 2
 12         # 3 * 2 * 2
  5         # 5
 10         # 5 * 2
 20         # 5 * 2 * 2
 15         # 5 * 3
 30         # 5 * 3 * 2
 60         # 5 * 3 * 2 * 2

julia> divisors(-10)
4-element Vector{Int64}:
  1
  2
  5
 10

julia> divisors(0)
Int64[]
```
