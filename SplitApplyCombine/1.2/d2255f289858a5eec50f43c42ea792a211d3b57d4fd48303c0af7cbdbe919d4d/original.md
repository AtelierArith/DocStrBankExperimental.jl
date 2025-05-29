```
groupview([by], container)
```

Like `group`, but each grouping is a `view` of the indexable input `container`.

# Example

```jldoctest
julia> v = [3,4,2,6,5,8]
6-element Array{Int64,1}:
 3
 4
 2
 6
 5
 8

julia> groups = groupview(iseven, v)
2-element GroupDictionary{Bool,SubArray{Int64,1,Array{Int64,1},Tuple{Array{Int64,1}},false},Array{Int64,1},Dictionary{Bool,Array{Int64,1}}}
 false │ [3, 5]
  true │ [4, 2, 6, 8]

julia> groups[false] .= 99  # set all the odd values to 99
2-element view(::Array{Int64,1}, [1, 5]) with eltype Int64:
 99
 99

julia> v
6-element Array{Int64,1}:
 99
  4
  2
  6
 99
  8
```
