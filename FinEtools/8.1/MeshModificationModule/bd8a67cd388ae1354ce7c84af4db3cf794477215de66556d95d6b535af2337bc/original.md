```
nodepartitioning(fens::FENodeSet, fesarr, npartitions::Vector{Int})
```

Compute the inertial-cut partitioning of the nodes.

`fesarr` = array of finite element sets that represent regions `npartitions` = array of the number of partitions in each region. However note that the actual number of partitions will be a power of two.

The partitioning itself is carried out by `nodepartitioning()` with a list of nodes to be included in the partitioning. For each region I the nodes included in the partitioning are those connected to the elements of that region, but not to elements that belong to any of the previous regions, 1…I-1.
