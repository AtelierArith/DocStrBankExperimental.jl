```
scatter_add(a::PyObject, 
    indices::Union{Colon, Int64, Array{Int64}, BitArray{1}, Array{Bool,1}, UnitRange{Int64}, StepRange{Int64, Int64}, PyObject},
    updates::Union{Array{<:Real}, Real, PyObject})
```

Updates array `add`

```
a[indices] += updates
```

# Example

Julia:

```julia
A[[1;2;3]] += rand(3)
A[2] += 1.0
```

ADCME:

```
A = scatter_add(A, [1;2;3], rand(3))
A = scatter_add(A, 2, 1.0)
```
