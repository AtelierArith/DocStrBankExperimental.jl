```
LefschetzComplex
```

Collect the Lefschetz complex information in a struct.

The struct is created via the following fields:

  * `labels::Vector{String}`: Vector of labels associated with cell indices
  * `dimensions::Vector{Int}`: Vector cell dimensions
  * `boundary::SparseMatrix`: Boundary matrix, columns give the cell boundaries

It is expected that the dimensions are given in increasing order, and that the square of the boundary matrix is zero. Otherwise, exceptions are raised. In addition, the following fields are created during initialization:

  * `ncells::Int`: Number of cells
  * `dim::Int`: Dimension of the complex
  * `indices::Dict{String,Int}`: Dictionary for finding cell index from label

The coefficient field is specified by the boundary matrix.

!!! warning
    Note that the constructor does not check whether the boundary matrix squares to zero. It is the responsibility of the user to ensure that!

