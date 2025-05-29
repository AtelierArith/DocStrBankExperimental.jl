```
SparseMatrixExp{N}
```

Type that represents the matrix exponential, $\exp(M)$, of a sparse matrix.

### Fields

  * `M` – sparse square matrix

### Examples

Take for example a random sparse matrix of dimensions $100 × 100$ and with occupation probability $0.1$:

```jldoctest SparseMatrixExp_constructor
julia> using SparseArrays

julia> A = sprandn(100, 100, 0.1);

julia> using ExponentialUtilities

julia> E = SparseMatrixExp(A);

julia> size(E)
(100, 100)
```

Here `E` is a lazy representation of $\exp(A)$. To compute with `E`, use `get_row` and `get_column` resp. `get_rows` and `get_columns`. These functions return row and column vectors (or matrices). For example:

```jldoctest SparseMatrixExp_constructor
julia> get_row(E, 10);  # compute E[10, :]

julia> get_column(E, 10);  # compute E[:, 10]

julia> get_rows(E, [10]);  # same as get_row(E, 10), but yields a 1x100 matrix

julia> get_columns(E, [10]);  # same as get_column(E, 10), but yields a 100x1 matrix
```

### Notes

This type is provided for use with large and sparse matrices. The evaluation of the exponential matrix action over vectors relies on external packages such as [ExponentialUtilities](https://github.com/SciML/ExponentialUtilities.jl) or [Expokit](https://github.com/acroy/Expokit.jl). Hence, you will have to install and load such an optional dependency to have access to the functionality of `SparseMatrixExp`.
