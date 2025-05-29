```
scatter_update(A::PyObject, 
    xind::Union{Colon, Int64, Array{Int64}, BitArray{1}, Array{Bool,1}, UnitRange{Int64}, StepRange{Int64, Int64}, PyObject},
    yind::Union{Colon, Int64, Array{Int64}, BitArray{1}, Array{Bool,1}, UnitRange{Int64}, StepRange{Int64, Int64}, PyObject},
    updates::Union{Array{<:Real}, Real, PyObject})
```

```julia
A[xind, yind] = updates
```
