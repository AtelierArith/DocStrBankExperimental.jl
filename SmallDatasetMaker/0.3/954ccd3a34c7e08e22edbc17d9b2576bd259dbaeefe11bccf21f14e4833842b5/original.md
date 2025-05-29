`tryparse_summary(v::AbstractVector, typetoparse::Type{<:Any})`

# Example

```jldoctest
julia> tryparse_summary(["1", "2", "3.3", 10, "NaN"], Float64) .|> typeof
5-element Vector{DataType}:
 SmallDatasetMaker.NotException
 SmallDatasetMaker.NotException
 SmallDatasetMaker.NotException
 MethodError
 SmallDatasetMaker.NotException
```
