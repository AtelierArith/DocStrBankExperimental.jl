```
maximal_subgroups(num::Integer, AG::Type{<:AbstractGroup}=SpaceGrop{3}; kind)
```

Returns the graph structure of the maximal subgroups as a `GroupRelationGraph` for a group of type `AG` and number `num`.

## Visualization

The resulting group structure can be plotted using Makie.jl (e.g., GLMakie.jl) using `plot(::GroupRelationGraph)`:

```jl
julia> using Crystalline
julia> gr = maximal_subgroups(112, SpaceGroup{3})
julia> using GraphMakie, GLMakie
julia> plot(gr)
```

## Keyword arguments

  * `kind` (default, `Crystalline.TRANSLATIONENGLEICHE`): to return klassengleiche relations, set `kind = Crystalline.KLASSENGLEICHE`). For klassengleiche relationships, only a selection of reasonably low-index relationships are returned.

## Data sources

The group relationships returned by this function were retrieved from the Bilbao Crystallographic Server's [MAXSUB](https://www.cryst.ehu.es/cryst/maxsub.html) program. Please cite the original reference work associated with MAXSUB:

  * Aroyo et al., [Z. Kristallogr. Cryst. Mater. **221**, 15 (2006)](https://doi.org/10.1524/zkri.2006.221.1.15).
