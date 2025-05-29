```
SplitAxis(ax::AbstractUnitRange, n::Real)
```

Split `ax` into `ceil(Int, n)` approximately equal-sized chunks. The first chunk is no larger than any other chunk, and any fractional "deficit" in `n` will further shrink the first chunk.

This can be useful in splitting work across threads. When the first thread is responsible for assigning work to the others, it's often useful to assign less work to it to account for the time spent scheduling.

# Examples

```jldoctest; setup=:(using TiledIteration)
julia> collect(SplitAxis(1:16, 4))
4-element Vector{UnitRange{Int64}}:
 1:4
 5:8
 9:12
 13:16

julia> collect(SplitAxis(1:16, 3.5))
4-element Vector{UnitRange{Int64}}:
 1:1
 2:6
 7:11
 12:16
```

In the latter case all the ranges except the first have length 5; consequently, only one element remains for the first chunk.
