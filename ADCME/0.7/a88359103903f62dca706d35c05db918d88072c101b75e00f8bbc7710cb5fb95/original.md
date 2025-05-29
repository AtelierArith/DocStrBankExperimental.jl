```
mpi_SparseTensor(rows::Union{Array{Int32,1}, PyObject}, ncols::Union{Array{Int32,1}, PyObject}, cols::Union{Array{Int32,1}, PyObject},
    vals::Union{Array{Float64,1}, PyObject}, ilower::Int64, iupper::Int64, N::Int64)
```

Create a $N\times N$ distributed sparse tensor `A` for the current MPI processor. The current MPI processor owns rows with indices `[ilower, iupper]`. The submatrix is specified using the CSR format. 

  * `rows`: an array indicating the rows that contain nonzero values. Note `rows ≥ ilower`.
  * `ncols`: an array indicating the number of nonzero values for each row in `rows`.
  * `cols`: the column indices for nonzero values. Its length is $\sum_{i=1}^{\mathrm{ncols}} \mathrm{ncols}_i$
  * `vals`: the nonzero values corresponding to each column index in `cols`

Note that by default the indices are zero-based. 
