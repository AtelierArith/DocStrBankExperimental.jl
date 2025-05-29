```
SparseMatrixCOO(is::Vector, js::Vector, vs::Vector, m::Int, n::Int) -> SparseMatrixCOO
SparseMatrixCOO{Tv, Ti}(is::Vector{Ti}, js::Vector{Ti}, vs::Vector{Tv}, m::Int, n::Int) -> SparseMatrixCOO
```

A sparse matrix in COOrdinate format.

Values `vs` are added to the matrix at rows `is` and columns `js` in a matrix with `m` rows and `n` columns.

Also known as the ‘ijv’ or ‘triplet’ format.

# Notes

COO matrices should not be used in arithmetic operations like addition, subtraction, multiplication, division, and matrix power.

### Advantages of the COO format

  * facilitates fast conversion among sparse formats
  * permits duplicate entries (see example)
  * very fast conversion to and from CSR/CSC formats (CSR is not implemented)

### Disadvantages of the COO format

does not directly support:

  * arithmetic operations
  * slicing

### Intended Usage

  * COO is a fast format for constructing sparse matrices
  * Once a matrix has been constructed, convert to CSR or CSC format for fast arithmetic and matrix vector operations
  * By default when converting to CSR or CSC format, duplicate (i,j) entries will be summed together. This facilitates efficient construction of finite element matrices and the like. (see example)

# Example

```julia-repl
julia> SparseMatrixCOO([4,3,1,2,2], [2,3,1,4,4], [1,2,3,4,5], 4,4) # duplicate entries at (2,4) summed together
4×4 SparseMatrixCOO{Int64, Int64}:
 3  0  0  0
 0  0  0  9
 0  0  2  0
 0  1  0  0

```
