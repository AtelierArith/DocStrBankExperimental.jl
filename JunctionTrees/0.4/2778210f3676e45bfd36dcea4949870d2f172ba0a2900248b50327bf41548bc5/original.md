```julia
norm(A::JunctionTrees.Factor{T, N}) -> JunctionTrees.Factor

```

Normalize the values in Factor A such they sum up to 1.

# Examples

```jldoctest
A = Factor{Float64,2}((1, 2), [0.2 0.4; 0.6 0.8])
norm(A)

# output

Factor{Float64, 2}((1, 2), [0.1 0.2; 0.3 0.4])
```
