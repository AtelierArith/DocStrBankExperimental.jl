```
Clustering
```

The clustering algorithm used to group atoms into vertices.

This choice only affects the creation of a `UnderlyingNets` from a `Crystal`, not the `Crystal` itself, and in particular not the bond detection algorithm.

The basic choices are:

  * `Auto`: determined using the [`StructureType`](@ref).
  * `Input`: use the input residues as vertices. Fail if some atom does not belong to a residue.
  * `EachVertex`: each atom is its own vertex. Vertices with degree 2 or lower are iteratively collapsed into edges until all vertices have degree 3 or more.

The next clustering options are designed for MOFs but may target other kinds of frameworks. In all cases, the clusters are refinements on top of already-defined clusters, such as the organic and inorganic SBUs defined by the `MOF` structure. Except for `AllNodes`, infinite clusters (such as the inorganic clusters in a rod MOF) are split into new finite clusters using heuristics.

  * `SingleNodes`: each already-defined cluster is mapped to a vertex.
  * `AllNodes`: keep points of extension for organic clusters.
  * `Standard`: make each metallic atom its own vertex and do not bond those together if they share a common non-metallic neighbour.
  * `PE`: stands for Points of Extension. Keep points of extension for organic clusters, remove metallic centres and bond their surrounding points of extension.
  * `PEM`: stands for Points of Extension and Metals. Keep points of extension for organic clusters and each metal centre as a separate vertex.
