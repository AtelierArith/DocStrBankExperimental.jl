```
shell_cluster_partitioning(fens, fes, nelperpart = 50, crease_ang = 30/180*pi, cluster_max_normal_deviation = 2 * crease_ang)
```

Compute the coarse grid (cluster) partitioning of a shell structure.

The elements are partitioned into subsets with `ShellStructureTopo.create_partitions()` based on the number of elements per partition (`nelperpart`). Then the nodes of the element subsets are assigned to clusters.
