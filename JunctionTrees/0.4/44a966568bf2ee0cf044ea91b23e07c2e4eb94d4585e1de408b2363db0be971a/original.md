```julia
sum(
    A::JunctionTrees.Factor{T, ND},
    V::NTuple{N, Int64} where N
) -> JunctionTrees.Factor

```

Sum out the variables in `V` from factor A.

# Examples

```jldoctest
A = Factor{Float64,2}((1, 2), [0.59 0.41; 0.22 0.78])
sum(A, (2,))

# output

Factor{Float64, 1}((1,), [1.0, 1.0])
```
