```
groupsimplices(groupby::AbstractVector)
```

Create SimplexGraph connecting elements with identical values in the groupby vector.

# Examples

```
julia> sg = groupsimplices(["A","A","B","C","B"]);

julia> sg.G
5×3 BitArray{2}:
 1  0  0
 1  0  0
 0  1  0
 0  0  1
 0  1  0

julia> sg.w
3-element Array{Int64,1}:
 2
 2
 1
```
