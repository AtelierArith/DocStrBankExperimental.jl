`srgcd(a::Pol,b::Pol)`

sub-resultant gcd: gcd of polynomials over a unique factorization domain

```julia-repl
julia> srgcd(4q+4,6q^2-6)
Pol{Int64}: 2q+2
```

See Knuth AOCP2 4.6.1 Algorithm C
