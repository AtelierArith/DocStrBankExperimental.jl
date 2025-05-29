```
GridSpace(d::NTuple{D, Int}; periodic = true, metric = :chebyshev)
```

Create a `GridSpace` that has size given by the tuple `d`, having `D ≥ 1` dimensions. Optionally decide whether the space will be periodic and what will be the distance metric. The position type for this space is `NTuple{D, Int}`, use [`GridAgent`](@ref) for convenience. Valid positions have indices in the range `1:d[i]` for the `i`-th dimension.

An example using `GridSpace` is [Schelling's segregation model](@ref Tutorial).

## Distance specification

The typical terminology when searching neighbors in agent based modelling is "Von Neumann" neighborhood or "Moore" neighborhoods. However, because Agents.jl provides a much more powerful infrastructure for finding neighbors, both in arbitrary dimensions but also of arbitrary neighborhood size, this established terminology is no longer appropriate. Instead, distances that define neighborhoods are specified according to a proper metric space, that is both well defined for any distance, and applicable to any dimensionality.

The allowed metrics are (and see docs online for a plotted example):

  * `:chebyshev` metric means that the `r`-neighborhood of a position are all positions within the hypercube having side length of `2*floor(r)` and being centered in the origin position. This is similar to "Moore" for `r = 1` and two dimensions.
  * `:manhattan` metric means that the `r`-neighborhood of a position are all positions whose cartesian indices have Manhattan distance `≤ r` from the cartesian index of the origin position. This similar to "Von Neumann" for `r = 1` and two dimensions.
  * `:euclidean` metric means that the `r`-neighborhood of a position are all positions whose cartesian indices have Euclidean distance `≤ r` from the cartesian index of the origin position.

## Advanced dimension-dependent distances in Chebyshev metric

If `metric = :chebyshev`, some advanced specification of distances is allowed when providing `r` to functions like [`nearby_ids`](@ref).

1. `r::NTuple{D,Int}` such as `r = (5, 2)`. This would mean a distance of 5 in the first dimension and 2 in the second. This can be useful when different coordinates in the space need to be searched with different ranges, e.g., if the space corresponds to a full building, with the third dimension the floor number.
2. `r::Vector{Tuple{Int,UnitRange{Int}}}` such as `r = [(1, -1:1), (3, 1:2)]`. This allows explicitly specifying the difference between position indices in each specified dimension. The example `r = [(1, -1:1), (3, 1:2)]` when given to e.g., [`nearby_ids`](@ref), would search dimension 1 one step of either side of the current position (as well as the current position since `0 ∈ -1:1`) and would search the third dimension one and two positions above current. Unspecified dimensions (like the second in this example) are searched throughout all their possible ranges.

See the [Battle Royale](https://juliadynamics.github.io/AgentsExampleZoo.jl/dev/examples/battle/) example for usage of this advanced specification of dimension-dependent distances where one dimension is used as a categorical one.
