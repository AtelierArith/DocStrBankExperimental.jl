`factor(f::Pol{<:Union{Integer,Rational{<:Integer}}})`

Factor `f` over the rationals. The result is a `Primes.Factorization{typeof(f)}`.

```julia-repl
julia> factor(Pol(:q)^24-1)
(q-1) * (q²-q+1) * (q⁴-q²+1) * (q⁸-q⁴+1) * (q⁴+1) * (q²+1) * (q+1) * (q²+q+1)
```
