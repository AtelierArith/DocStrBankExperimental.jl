```
CubicGrid(dims::NTuple{D,Int}, fold::NTuple{D,Bool})
```

Represents a `D`-dimensional grid. Used to define a cubic lattice and boundary conditions for some [`AbstractHamiltonian`](@ref)s, e.g. with the keyword argument `geometry` when constructing a [`HubbardRealSpace`](@ref). The type instance can be used to convert between cartesian vector indices (tuples or `SVector`s) and linear indices (integers). When indexed with vectors, it folds them back into the grid if the out-of-bounds dimension is periodic and 0 otherwise (see example below).

  * `dims` controls the size of the grid in each dimension.
  * `fold` controls whether the boundaries in each dimension are periodic (or folded in the case of momentum space).

```julia
julia> geo = CubicGrid((2,3), (true,false))
CubicGrid{2}((2, 3), (true, false))

julia> geo[1]
(1, 1)

julia> geo[2]
(2, 1)

julia> geo[3]
(1, 2)

julia> geo[(1,2)]
3

julia> geo[(3,2)] # 3 is folded back into 1
3

julia> geo[(3,3)]
5

julia> geo[(3,4)] # returns 0 if out of bounds
0
```

See also [`PeriodicBoundaries`](@ref), [`HardwallBoundaries`](@ref) and [`LadderBoundaries`](@ref) for special-case constructors. See also [`HubbardRealSpace`](@ref) and [`G2RealSpace`](@ref).
