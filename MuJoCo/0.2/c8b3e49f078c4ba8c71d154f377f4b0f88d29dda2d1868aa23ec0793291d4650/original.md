```
mj_addM(m, d, dst, rownnz, rowadr, colind)
```

Add inertia matrix to destination matrix. Destination can be sparse uncompressed, or dense when all int* are NULL

# Arguments

  * **`m::Model`** -> Constant.
  * **`d::Data`**
  * **`dst::Vector{Float64}`** -> A vector of variable size. `dst` should be a vector, not a matrix. `dst` should be of size nM.
  * **`rownnz::Vector{Int32}`** -> A vector of variable size. `rownnz` should be a vector, not a matrix. `rownnz` should be of size nv.
  * **`rowadr::Vector{Int32}`** -> A vector of variable size. `rowadr` should be a vector, not a matrix. `rowadr` should be of size nv.
  * **`colind::Vector{Int32}`** -> A vector of variable size. `colind` should be a vector, not a matrix. `colind` should be of size nM.
