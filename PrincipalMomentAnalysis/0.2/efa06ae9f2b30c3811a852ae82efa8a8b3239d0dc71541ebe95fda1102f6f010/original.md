```
SimplexGraph{T<:AbstractMatrix{Bool}, S<:Union{Number,AbstractVector{<:Number}}}
```

Struct describing a set of simplices with vertices numbered from 1:N. Optionally, each simplex can be assigned a weight.

## Usage

```
SimplexGraph(G, w=true)
```

Construct a SimplexGraph. `G` is a `MxN` matrix of booleans, where `M` is the number of vertices and `N` is the number of simplices. Each column in `G` represents one simplex. True means that a vertex is part of the simplex and false that it is not. Optionally, a vector `w` of length N can be used to specify a weight (total mass) for each simplex. The weight defaults to 1 (true).

See also `pma`, `groupsimplices`, `timeseriessimplices`, `neighborsimplices`.
