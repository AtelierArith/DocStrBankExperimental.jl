`valuation(c::Union{Integer,Rational{<:Integer},p::Integer)`  `p`-adic  valuation of `c` (largest  power of `p` which  divides `c`; for a `Rational`, valuation of the numerator minus that of the denominator).

```julia-repl
julia> valuation.(24,(2,3,5))
(3, 1, 0)
```
