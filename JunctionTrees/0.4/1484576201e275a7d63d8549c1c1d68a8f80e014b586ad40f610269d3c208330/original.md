```julia
sum(
    A::JunctionTrees.Factor,
    V::Int64...
) -> JunctionTrees.Factor

```

Sum out an arbitrary number of variables from factor A.

# Examples

```jldoctest
A = Factor{Float64,3}((1, 2, 3), cat([0.25 0.08; 0.05 0.0; 0.15 0.09],
                                     [0.35 0.16; 0.07 0.0; 0.21 0.18], dims=3))
sum(A, 1, 2)

# output

Factor{Float64, 1}((3,), [0.6199999999999999, 0.97])
```
