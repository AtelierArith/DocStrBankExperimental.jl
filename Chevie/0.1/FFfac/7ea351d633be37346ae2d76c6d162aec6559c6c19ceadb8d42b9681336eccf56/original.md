`factor(f::Pol{FFE{p}}[, F])`

Given  `f` a polynomial  over a finite  field of characteristic `p`, factor `f`,  by default over the  field of its coefficients,  or if specified over the field `F`. The result is a `Primes.Factorization{Pol{FFE{p}}}`.

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
