```
seg2 = merge_segments(seg, threshold)
```

Merges segments in a [`SegmentedImage`](@ref) by building a region adjacency graph (RAG) and merging segments connected by edges with weight less than  `threshold`.

# Arguments:

  * `seg`         : SegmentedImage to be merged.
  * `threshold`   : Upper bound of the adjacent segment color difference to                  consider merging segments.

# Citation:

Vighnesh Birodkar "Hierarchical merging of region adjacency graphs" https://vcansimplify.wordpress.com/2014/08/17/hierarchical-merging-of-region-adjacency-graphs/
