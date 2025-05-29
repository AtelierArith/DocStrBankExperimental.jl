`root(x,n=2)`

は、`x` の `n` 番目の根を計算します。私たちは、単位根の `n` 番目の根や、整数または有理数の完全な `n` 番目の累乗の `n` 番目または `2n` 番目の根を計算する方法を知っています。

```julia-repl
julia> root(-1)
Cyc{Int64}: ζ₄

julia> root(E(4))
Root1: ζ₈

julia> root(27//8,6)
Cyc{Rational{Int64}}: √6/2
```
