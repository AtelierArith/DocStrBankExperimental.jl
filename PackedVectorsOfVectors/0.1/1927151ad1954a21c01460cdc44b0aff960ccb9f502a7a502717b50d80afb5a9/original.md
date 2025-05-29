```
PackedVectorOfVectors{P,V,E} <: AbstractVector{E}
```

Vector of vectors, stored as a single long vector `v::V` and a vector of pointers `p::P` indicating the subvector boundaries.

`PackedVectorOfVectors` is roughly equivalent to `SparseMatrixCSC` without the `rowval` vector.
