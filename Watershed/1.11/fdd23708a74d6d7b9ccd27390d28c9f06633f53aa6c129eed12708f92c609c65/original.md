`REGIONGRAPH` - create region graph by finding maximum affinity between each pair of regions in segmentation

```
 rg = regiongraph(aff,seg,max_segid)
```

  * `rg`: region graph as list of edges, array of (weight,id1,id2) tuples. The edges are sorted so that weights are in descending order.
  * `aff`: affinity graph (undirected and weighted). 4D array of affinities, where last dimension is of size 3
  * `seg`: segmentation.  Each element of the 3D array contains a *segment ID*, a nonnegative integer ranging from 0 to `max_segid`
  * `max_segid`: number of segments

The vertices of the region graph are regions in the segmentation.  An edge of the region graph corresponds to a pair of regions in the segmentation that are connected by an edge in the affinity graph.  The weight of an edge in the region graph is the maximum weight of the edges in the affinity graph connecting the two regions.

The region graph includes every edge between a region and itself. The weight of a self-edge is the maximum affinity within the region.

Background voxels (those with ID=0) are ignored.
