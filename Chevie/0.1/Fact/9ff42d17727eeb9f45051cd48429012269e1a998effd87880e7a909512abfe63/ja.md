`factor(f::Pol{<:Union{Integer,Rational{<:Integer}}})`

有理数の下で `f` を因数分解します。結果は `Primes.Factorization{typeof(f)}` です。

```julia-repl
julia> factor(Pol(:q)^24-1)
(q-1) * (q²-q+1) * (q⁴-q²+1) * (q⁸-q⁴+1) * (q⁴+1) * (q²+1) * (q+1) * (q²+q+1)
```
