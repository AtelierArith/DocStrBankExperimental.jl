```
hardwiredclusters(net::HybridNetwork, taxon_labels)
```

Returns a matrix describing all the hardwired clusters in a network, with taxa listed in same order as in `taxon_labels` to describe their membership in each cluster. Allows for missing taxa, with entries all 0.

Warnings:

  * clusters are rooted, so the root must be correct.
  * each hybrid node is assumed to have exactly 2 parents (no more).

Each row corresponds to one internal edge, that is, external edges are excluded. If the root is a leaf node, the external edge to that leaf is included (first row). Both parent hybrid edges to a given hybrid node only contribute a single row (they share the same hardwired cluster).

  * first column: edge number
  * next columns: 0/1. 1=descendant of edge, 0=not a descendant, or missing taxon.
  * last column:  10/11 values. 10=tree edge, 11=hybrid edge

See also [`hardwiredclusterdistance`](@ref) and [`hardwiredcluster`](@ref).
