```
gather(snd;destination=MAIN)
```

Return an array whose first entry contains a copy of the elements of array `snd` collected in a vector. Another component different from the first one can be used to store the result by setting the optional key-word argument `destination`. Setting `destination=:all`, will store the result in all entries of `rcv` resulting in a "gather all" operation.

# Examples

```jldoctest
julia> using PartitionedArrays

julia> snd = collect(1:3)
3-element Vector{Int64}:
 1
 2
 3

julia> gather(snd,destination=3)
3-element Vector{Vector{Int64}}:
 []
 []
 [1, 2, 3]

julia> gather(snd,destination=:all)
3-element Vector{Vector{Int64}}:
 [1, 2, 3]
 [1, 2, 3]
 [1, 2, 3]
```
