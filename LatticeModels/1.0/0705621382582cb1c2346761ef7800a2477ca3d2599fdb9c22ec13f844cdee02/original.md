```
AdjacencyMatrix{LT} where {LT<:Lattice}
```

Represents the bonds on some lattice.

---

```
AdjacencyMatrix(lat[, mat])
```

Construct an adjacency matrix from the `mat` matrix on the `lat` lattice.

If `mat` is not provided, it is assumed to be a zero matrix.

## Example

```jldoctest
julia> using LatticeModels

julia> l = SquareLattice(2, 2);

julia> a = AdjacencyMatrix(l)
Adjacency matrix on 4-site SquareLattice in 2D space
Values in a 4×4 SparseArrays.SparseMatrixCSC{Bool, Int64} with 0 stored entries:
 ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅

julia> site1, site2, site3, site4 = l;

julia> a[site1, site2] = a[site2, site4] = a[site3, site4] = true;

julia> a
Adjacency matrix on 4-site SquareLattice in 2D space
Values in a 4×4 SparseArrays.SparseMatrixCSC{Bool, Int64} with 6 stored entries:
 ⋅  1  ⋅  ⋅
 1  ⋅  ⋅  1
 ⋅  ⋅  ⋅  1
 ⋅  1  1  ⋅
```
