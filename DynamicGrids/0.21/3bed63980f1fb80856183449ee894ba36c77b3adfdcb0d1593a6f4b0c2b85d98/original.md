```
Neighbors <: NeighborhoodRule

Neighbors(f, neighborhood=Moor(1))
Neighbors{R,W}(f, neighborhood=Moore())
```

A [`NeighborhoodRule`](@ref) that receives a [`Neighborhood`](@ref) object  for the first `R` grid, followed by the cell value/s for the required grids,  as with [`Cell`](@ref).

Returned value(s) are written to the `W` grid/s.

As with all [`NeighborhoodRule`](@ref), you do not have to check bounds at grid edges, that is handled for you internally.

Using [`SparseOpt`](@ref) may improve neighborhood performance when a specific value (often zero) is common and can be safely ignored.

## Example

Runs a game of life glider on grid `:a`:

```jldoctest
using DynamicGrids
const sum_states = (0, 0, 1, 0, 0, 0, 0, 0, 0), 
                   (0, 0, 1, 1, 0, 0, 0, 0, 0)
life = Neighbors{:a}(Moore(1)) do data, hood, a, I
    sum_states[a + 1][sum(hood) + 1]
end
init = Bool[
     0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
     0 0 0 0 0 1 1 1 0 0 0 0 0 0 0
     0 0 0 0 0 0 0 1 0 0 0 0 0 0 0
     0 0 0 0 0 0 1 0 0 0 0 0 0 0 0
     0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
]
output = REPLOutput((; a=init); fps=25, tspan=1:50)
sim!(output, Life{:a}(); boundary=Wrap())
output[end][:a]

# output
5×15 Matrix{Bool}:
 0  0  1  0  1  0  0  0  0  0  0  0  0  0  0
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
 0  0  0  1  0  0  0  0  0  0  0  0  0  0  0
 0  0  0  1  1  0  0  0  0  0  0  0  0  0  0

```
