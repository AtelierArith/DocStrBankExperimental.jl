`MST` - compute maximal spanning tree from weighted graph

```
 regiontree = mst(rg,max_segid)
```

  * `rg`: region graph as list of edges, array of (weight,id1,id2) tuples.  The edges should be presorted so that weights are in descending order.
  * `max_segid`: largest ID in region graph
  * `regiontree`: *maximal* spanning tree (MST) of region graph as list of edges, array of `(weight,id1,id2)` tuples. The vertices in each edge are ordered so that `id2` is unique across edges. In other words, id1 and id2 correspond to parent and child in the tree. The code places the root of the tree at segid=1

The MST effectively represents the segmentPairsrogram for single-linkage clustering.  Each edge `(weight,id1,id2)` in the MST represents an internal vertex of the dendrogram located at height = `weight`, i.e., a merging of two clusters with score `weight`.  The MST contains a bit more information than the dendrogram, because `id1` and `id2` are the root IDs of the two clusters, i.e., the maximum weight edge between the two clusters is between their elements `id1` and `id2`.

The code should work for general graphs.  If edges of `rg` are presorted by ascending weight, the code will compute the *minimal* spanning tree rather than the maximal spanning tree.
