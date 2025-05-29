```
TableIndexedMatrix{T,M,R,C} <: AbstractMatrix{T}
```

Matrix with row and column indices that can be selected based on row values in a `Tables.jl`-compatible table respectively. This is useful when how elements are stored into the matrix are determined by the rows of the tables.

# Parameters

  * `T`: element type of the matrix.
  * `M`: type of the matrix.
  * `R`: type of the table paired with the row indices.
  * `C`: type of the table paired with the column indices.

# Fields

  * `m::M`: the matrix that stores the elements.
  * `r::R`: a table with the same number of rows with `m`.
  * `c::C`: a table of which the number of rows is equal to the number of columns of `m`.
