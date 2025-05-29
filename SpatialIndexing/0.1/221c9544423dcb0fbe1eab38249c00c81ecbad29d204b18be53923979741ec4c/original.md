R-Tree: `N`-dimensional spatial data index [guttman84].

R-tree groups data elements (`V`) into leaves (`Leaf`) and leaves into branches (`Branch`). It uses various heuristics to ensure that the minimal bounding rectangles (MBRs) of the nodes (`Rect{T,N}` rectangles that encompass the data elements attached to these nodes) stay compact and that the MBRs of the nodes that are on the same level of R-tree hierarchy have minimal overlap with each other. This property makes R-trees efficient for spatial queries.

To facilitate spatial indexing, the `V` data elements need to support `HasMBR` trait (i.e. define `mbrtype(V)` and `mbr(v::V)` methods) and, optionally, `HasID` trait (via `idtype(V)` and `id(v::V)` methods). `mbr(v::V)` should return minimal bounding rectangle (MBR) of type `Rect{T,N}` that contains `v`. `SpatialElem{T,N,D}` type provides generic implementation of spatial data element that explicitly stores `id`, `mbr` and data object of type `D` and implements `HasMBR` and `HasID` traits.

# Parameters

The behaviour of `RTree` is defined by the parameters supplied at its creation:

  * `T`: the numeric type for the spatial coordinate
  * `N`: the number of spatial dimensions
  * `variant`: one of `RTreeLinear`, `RTreeQuadratic`, or `RTreeStar` (default)
  * `tight_mbrs`: recalculate node MBR when the child is removed (default is `true`)
  * `branch_capacity`: capacity of branch nodes (default is `100`)
  * `leaf_capacity`: capacity of leaf nodes (default is `100`)
  * `leafpool_capacity`: How many detached 1st level nodes (leaves) should be kept for reuse (default is `100`)
  * `twigpool_capacity`: How many detached 2nd level nodes should be kept for reuse (default is `100`)
  * `branchpool_capacity`: How many other (level > 2) detached branch nodes should be kept for reuse (default is `100`)
  * `nearmin_overlap`: How many candidates to consider when identifying the node with minimal overlap (default is `32`)
  * `fill_factor`: How much should the node be filled (fraction of its capacity) after splitting (default is `0.7`)
  * `split_factor`: How much can the sizes of the two nodes differ after splitting (default is `0.4`)
  * `reinsert_factor`: How much should the node be underfilled (fraction of its capacity) to consider removing it and redistributing its children to other nodes (default is `0.3`)

# Performance

The nodes in R-tree have limited capacity (maximual number of children) specified at `RTree` creation (`leaf_capacity` and `branch_capacity`). Larger capacities results in shorter trees, but they time required to locate the specific spatial region grows linearly with the capacity.

# References

[guttman84] “R-Trees: A Dynamic Index Structure for Spatial Searching”     A. Guttman, Proc. 1984 ACM-SIGMOD Conference on Management of     Data (1985), 47-57. [beckmann90] "The R*-tree: an efficient and robust access method for points and rectangles"     N. Beckmann, H.P. Kriegel, R. Schneider, B. Seeger, Proc. 1990 ACM SIGMOD     international conference on Management of data (1990), p.322
