```
isprime(x::BigInt, [reps = 25]) -> Bool
```

Probabilistic primality test. Returns `true` if `x` is prime with high probability (pseudoprime); and `false` if `x` is composite (not prime). The false positive rate is about `0.25^reps`. `reps = 25` is considered safe for cryptographic applications (Knuth, Seminumerical Algorithms).

is*probably*prime is inherited from the module IntegerMathUtils that provides a wrapper to access functionality from the  GNU Multiple Precision Arithmetic Library (GMP) library

```julia
julia> isprime(big(3))
true
```
