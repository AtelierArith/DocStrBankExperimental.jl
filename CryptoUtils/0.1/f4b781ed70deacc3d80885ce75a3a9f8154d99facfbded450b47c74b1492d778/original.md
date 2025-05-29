```
sqrt_mod_prime(a::Integer, p::Integer) -> Integer
```

Solves `x^2 == a mod p` and returns one of the square roots `r`. The other root is `p - r`. If there are no solutions, throws an exception.

```julia
julia> sqrt_mod_prime(33^2, 73)
33
```
