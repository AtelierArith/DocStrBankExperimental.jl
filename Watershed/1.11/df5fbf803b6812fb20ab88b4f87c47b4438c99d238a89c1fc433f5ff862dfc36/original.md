`MERGEREGIONS` - merge small regions by agglomerative clustering

```
new_rg = mergeregions(seg, rg, counts, thresholds, dust_size = 0)
```

  * `seg` - segmentation.  IDs of foreground regions are 1:length(counts).  ID=0 for background.  This is modified in place by the clustering.
  * `rg`: region graph as list of edges, array of (weight,id1,id2) tuples. The edges should be presorted so that weights are in descending order. Region IDs should be consistent with those in `seg`, except no zeros.
  * `new_rg`: new region graph after clustering, same format as `rg`.
  * `counts`: sizes of regions in `seg` (modified in place)
  * `thresholds`: sequence of (size*th,weight*th) pairs to be used for merging
  * `dust_size`: after merging, tiny regions less than dust_size to be eliminated by changing them to background voxels

Agglomerative clustering proceeds by considering the edges of the region graph in sequence.  If either region has size less than `size_th`, then merge the regions. When the weight of the edge in the region graph is less than or equal to `weight_th`, agglomeration proceeds to the next `(size_th,weight_th)` in `thresholds` or terminates if there is none.

# to-do: update code to include self-edges in `new_rg`
