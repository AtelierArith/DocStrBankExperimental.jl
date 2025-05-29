```julia
struct CTMRGEnv{C, T}
```

Corner transfer-matrix environment containing unit-cell arrays of corner and edge tensors. The last two indices of the arrays correspond to the row and column indices of the unit cell, whereas the first index corresponds to the direction of the corner or edge tensor. The directions are labeled in clockwise direction, starting from the north-west corner and north edge respectively.

Given arrays of corners `c` and edges `t`, they connect to the network tensors `P` at site `(r, c)` in the unit cell as:

```
   c[1,r-1,c-1]---t[1,r-1,c]----c[2,r-1,c+1]
   |              |             |
   t[4,r,c-1]-----P[r,c]--------t[2,r,c+1]
   |              |             |
   c[4,r+1,c-1]---t[3,r+1,c]----c[3,r+1,c+1]
```

Here `P` represents an effective local constituent tensor. This can either be a single rank-4 tensor, a pair of PEPS tensors, or a stack of PEPS-PEPO-PEPS tensors depending on the network being contracted.

## Fields

  * `corners::Array{C, 3} where C`: 4 x rows x cols array of corner tensors, where the first dimension specifies the spatial direction
  * `edges::Array{T, 3} where T`: 4 x rows x cols array of edge tensors, where the first dimension specifies the spatial direction
