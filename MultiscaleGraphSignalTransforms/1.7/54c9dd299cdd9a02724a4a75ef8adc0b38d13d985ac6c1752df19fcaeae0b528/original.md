```
function rs_to_region(rs::Matrix{Any}, tag::Matrix{Any})
```

From the imformation of rs, tag from GP, compute the tag_r matrix, which have the same size of dmatrix (expansion coefficient matrix). Each element indicates the place of the coefficient in the expansion tree.

### Input Arguments

  * `rs::Matrix{Any}`: rs from GP, showing information of the partition tree
  * `tag::Matrix{Any}`: tag from GP, indicating coefficients tag

### Output Arguments

  * `tag_r::Matrix{UInt64}`: showing information of the partition tree, same size as dmatrix
