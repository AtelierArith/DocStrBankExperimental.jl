```
pack([T,] vv) -> PackedVectorOfVectors
```

Convert the vector of vectors `vv` to its packed representation. If `T` is provided, then the elements of the nested vector are converted to this type.

# Example

```jldoctest
julia> pack([[1,2],[3]])
2-element pack(::Vector{Vector{Int64}}):
 [1, 2]
 [3]

julia> pack(Float64, [[1,2],[3]])
2-element pack(::Vector{Vector{Float64}}):
 [1.0, 2.0]
 [3.0]
```
