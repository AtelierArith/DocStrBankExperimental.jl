```
scatter_update(a::PyObject, 
    indices::Union{Colon, Int64, Array{Int64}, BitArray{1}, Array{Bool,1}, UnitRange{Int64}, StepRange{Int64, Int64}, PyObject},
    updates::Union{Array{<:Real}, Real, PyObject})
```

配列 `a` を更新します

```
a[indices] = updates
```

# 例

Julia:

```julia
A[[1;2;3]] = rand(3)
A[2] = 1.0
```

ADCME:

```
A = scatter_update(A, [1;2;3], rand(3))
A = scatter_update(A, 2, 1.0)
```
