```
CompGraph
CompGraph(input::AbstractVertex, output::AbstractVertex)
CompGraph(input::AbstractVector{<:AbstractVertex}, output::AbstractVertex)
CompGraph(input::AbstractVertex, output::AbstractVector{<:AbstractVertex})
```

Basic graph for computation. While not strictly neccessary to compute anything, it makes it easier to keep track of things.

# Examples

```jldoctest
julia> using NaiveNASlib

julia> v1 = inputvertex("in1", 1) + inputvertex("in2", 1);

julia> v2 = invariantvertex(x -> 3x, v1);

julia> CompGraph(inputs(v1), v2)(2,3) # (2 + 3) * 3
15

julia> CompGraph(inputs(v1), [v1, v2])(2,3)
(5, 15)
```
