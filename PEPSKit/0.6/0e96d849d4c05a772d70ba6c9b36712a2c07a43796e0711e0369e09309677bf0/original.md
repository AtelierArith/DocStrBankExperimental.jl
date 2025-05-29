```
InfinitePartitionFunction(A; unitcell=(1, 1))
```

Create an `InfinitePartitionFunction` by specifying a tensor and unit cell.

The unit cell is labeled as a matrix which means that any tensor in the unit cell, regardless if partition function tensor or environment tensor, is obtained by shifting the row and column index `[r, c]` by one, respectively:

```
   |            |          |
---C[r-1,c-1]---T[r-1,c]---T[r-1,c+1]---
   |            |          |
---T[r,c-1]-----AA[r,c]----AA[r,c+1]----
   |            |          |
---T[r+1,c-1]---AA[r+1,c]--AA[r+1,c+1]--
   |            |          |
```

The unit cell has periodic boundary conditions, so `[r, c]` is indexed modulo the size of the unit cell.
