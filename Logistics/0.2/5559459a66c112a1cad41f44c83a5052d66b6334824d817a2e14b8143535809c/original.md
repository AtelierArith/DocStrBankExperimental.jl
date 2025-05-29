```
complement(x::Logistic) :: Logistic
```

Compute the complement, i.e., the difference between one and the argument.

# Examples

```jldoctest
julia> complement(logisticate(0.2))
Logistic{Float64}(1.3862943611198906) ≈ 0.8

julia> 1 - logisticate(0.2)
0.8
```
