`factor(f::Pol{FFE{p}}[, F])`

与えられた `f` は、特性 `p` の有限体上の多項式であり、デフォルトではその係数の体上で `f` を因数分解します。指定された場合は、体 `F` 上で因数分解します。結果は `Primes.Factorization{Pol{FFE{p}}}` です。

```julia-repl
julia> @Pol q
Pol{Int64}: q

julia> f=q^3*(q^4-1)^2*Z(3)^0
Pol{FFE{3}}: q¹¹+q⁷+q³

julia> factor(f)
(q²+1)² * (q+1)² * (q-1)² * q³

julia> factor(f,GF(9))
(q+1)² * (q-1)² * (q+Z₉²)² * (q+Z₉⁶)² * q³
```
