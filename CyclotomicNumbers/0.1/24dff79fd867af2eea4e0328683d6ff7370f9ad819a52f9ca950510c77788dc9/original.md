`root(x,n=2)`

computes  an `n`-th root of `x`  when we know how to  do it. We know how to compute  `n`-th roots  of roots  of unity,  and `n`-th  or `2n`-th roots of perfect `n`-th powers of integers or rationals.

```julia-repl
julia> root(-1)
Cyc{Int64}: ζ₄

julia> root(E(4))
Root1: ζ₈

julia> root(27//8,6)
Cyc{Rational{Int64}}: √6/2
```
