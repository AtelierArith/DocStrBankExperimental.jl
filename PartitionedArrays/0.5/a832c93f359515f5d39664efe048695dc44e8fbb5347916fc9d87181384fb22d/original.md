```
scatter(snd;source=MAIN)
```

Copy the items in the collection `snd[source]` into an array of the same size and container type as `snd`. This function requires `length(snd[source]) == length(snd)`.

# Examples

```jldoctest
julia> using PartitionedArrays

julia> a = [Int[],[1,2,3],Int[]]
3-element Vector{Vector{Int64}}:
 []
 [1, 2, 3]
 []

julia> scatter(a,source=2)
3-element Vector{Int64}:
 1
 2
 3
```
