```
factor(n::Integer) -> Primes.Factorization
```

Compute the prime factorization of an integer `n`. The returned object, of type `Factorization`, is an associative container whose keys correspond to the factors, in sorted order. The value associated with each key indicates the multiplicity (i.e. the number of times the factor appears in the factorization).

```julia
julia> factor(100)
2^2 ⋅ 5^2
```

For convenience, a negative number `n` is factored as `-1*(-n)` (i.e. `-1` is considered to be a factor), and `0` is factored as `0^1`:

```julia
julia> factor(-9)
-1 ⋅ 3^2

julia> factor(0)
0

julia> collect(factor(0))
1-element Array{Pair{Int64,Int64},1}:
 0=>1
```
