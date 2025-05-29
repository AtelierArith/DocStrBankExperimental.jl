```
struct EmbeddedDiscretization{Dc,T} <: AbstractEmbeddedDiscretization
```

This structure contains all the required information to build integration `Triangulation`s  for a cut model.

## Constructors

```
cut(cutter::Cutter,background,geom)
```

## Properties

  * `bgmodel::DiscreteModel`: the background mesh
  * `geo::CSG.Geometry`: the geometry used to cut the background mesh
  * `subcells::SubCellData`: collection of cut subcells, attached to the background mesh
  * `subfacets::SubFacetData`: collection of cut facets, attached to the background mesh
  * `ls_to_bgcell_to_inoutcut::Vector{Vector{Int8}}`: list of IN/OUT/CUT states for each cell   in the background mesh, for each node in the geometry tree.
  * `ls_to_subcell_to_inoutcut::Vector{Vector{Int8}}`: list of IN/OUT/CUT states for each subcell   in the cut part of the mesh, for each node in the geometry tree.
  * `ls_to_subfacet_to_inoutcut::Vector{Vector{Int8}}`: list of IN/OUT/CUT states for each subfacet   in the cut part of the mesh, for each node in the geometry tree.

## Methods

  * [`Triangulation(cut::EmbeddedDiscretization,in_or_out)`](@ref)
  * [`EmbeddedBoundary(cut::EmbeddedDiscretization)`](@ref)
  * [`GhostSkeleton(cut::EmbeddedDiscretization)`](@ref)
