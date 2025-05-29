```
cluster_partitioning(fens, fes, element_labels, nelperpart)
```

Compute the coarse grid (cluster) partitioning.

The elements are partitioned into subsets of approximately equal size (`nelperpart`). Then the nodes of the element subsets are assigned to clusters.

The element subsets are determined by the `element_labels` array: The elements of a given label belong together.  Then the elements of the next subset are partitioned,  and so on. The elements of label 0 are partitioned last.
