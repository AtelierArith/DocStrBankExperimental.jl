```
scatter_sub(a::PyObject, 
    indices::Union{Colon, Int64, Array{Int64}, BitArray{1}, Array{Bool,1}, UnitRange{Int64}, StepRange{Int64, Int64}, PyObject},
    updates::Union{Array{<:Real}, Real, PyObject})
```

Updates array `a`

```
a[indices] -= updates
```

# Example

Julia:

```julia
A[[1;2;3]] -= rand(3)
A[2] -= 1.0
```

ADCME:

```
A = scatter_sub(A, [1;2;3], rand(3))
A = scatter_sub(A, 2, 1.0)
```
