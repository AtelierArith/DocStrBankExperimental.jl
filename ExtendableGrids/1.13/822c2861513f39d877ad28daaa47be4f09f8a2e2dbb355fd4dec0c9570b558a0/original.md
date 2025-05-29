```
check_partitioning(grid; 
                   verbose=true, 
                   cellpartonly=false)
```

Check correctness of cell partitioning, necessary for parallel assembly:

  * Check if every node belongs to one of the cell partitions
  * Check if no node belongs to two cell partitions of the same color at once

If `cellpartonly==false` check correctness of node partitioning necessary for parallel sparse matrix multiplication and ILU preconditioning

  * Check if no node belongs to two node partitions of the same color at once
  * Check if no node is a neighbor of nodes from two node partitions of the same color
