```
as_categorical(arr::AbstractArray)
```

Converts the input array to a CategoricalArray.

# Arguments

`arr`: Input array.

# Returns

CategoricalArray constructed from the input array.

# Examples

```jldoctest
julia> arr = ["A", "B", "C", "A", "B", "B", "D", "E", missing]
9-element Vector{Union{Missing, String}}:
 "A"
 "B"
 "C"
 "A"
 "B"
 "B"
 "D"
 "E"
 missing
 
julia> as_categorical(arr)
9-element CategoricalArrays.CategoricalArray{Union{Missing, String},1,UInt32}:
 "A"
 "B"
 "C"
 "A"
 "B"
 "B"
 "D"
 "E"
 missing
```
