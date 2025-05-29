```
no_combinations(n::Int64, k::Int64)
```

Compute the binomial coefficient of `n` observations and `k` groups, for big integers.

# Examples

```jldoctest
julia> no_combinations(1000000,100000)
7.333191945934207610471288280331309569215030711272858517142085449641265002716664e+141178
```
