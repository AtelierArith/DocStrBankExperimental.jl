```
reduce_tensor(A::AbstractArray{Elt, N}, hyper_index_groups::Array{Int64, 1})
```

Function to reduce the dimension of the given tensor assuming the given hyper edge groups. For example a diagonal matrix will have a single hyper edge group with both indices [1, 2]

```jldoctest
julia> reduce_tensor([[1, 0] [0, 2]], [[1, 2]])
2-element Vector{Int64}:
 1
 2
```
