```
multicast(snd;source=MAIN)
```

Copy `snd[source]` into a new array of the same size and type as `snd`.

# Examples

```jldoctest
julia> using PartitionedArrays

julia> a = [0,0,2,0]
4-element Vector{Int64}:
 0
 0
 2
 0

julia> multicast(a,source=3)
4-element Vector{Int64}:
 2
 2
 2
 2
```
