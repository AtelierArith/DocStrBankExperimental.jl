```
split_data(data::AbstractArray, i::Int64, N::Int64)
```

データをNセクションに分割し、i番目のセクションを返します

# 例

```jl
julia> split_data([1,2,3], 1, 2)
2-element Vector{Int64}:
 1
 2

julia> split_data([1,2,3], 2, 2)
1-element Vector{Int64}:
 3

julia> split_data([1,2,3], 3, 4)
1-element Vector{Int64}:
 3
```
