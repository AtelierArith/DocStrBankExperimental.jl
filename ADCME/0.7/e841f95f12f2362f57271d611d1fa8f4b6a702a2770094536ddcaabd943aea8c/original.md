```
mutable struct mpi_SparseTensor
    rows::PyObject 
    ncols::PyObject
    cols::PyObject 
    values::PyObject 
    ilower::Int64 
    iupper::Int64 
    N::Int64
    oplibpath::String
end
```

A structure to hold local data of a sparse matrix. The global matrix is assumed to be a $M\times N$ square matrix.  The current processor owns rows from `ilower` to `iupper` (inclusive). The data is specified by 

  * `rows`: an array indicating the rows that contain nonzero values. Note `rows ≥ ilower`.
  * `ncols`: an array indicating the number of nonzero values for each row in `rows`.
  * `cols`: the column indices for nonzero values. Its length is $\sum_{i=1}^{\mathrm{ncols}} \mathrm{ncols}_i$
  * `vals`: the nonzero values corresponding to each column index in `cols`
  * `oplibpath`: the backend library (returned by `ADCME.load_plugin_MPITensor`)

All data structure are 0-based. Note if we work with a linear solver, $M=N$.

For example, consider the sparse matrix 

```
[  1 0 0 1  ]
[  0 1 2 1  ]
```

We have 

```julia
rows = Int32[0;1]
ncols = Int32[2;3]
cols = Int32[0;3;1,2,3]
values = [1.;1.;1.;2.;1.]
iupper = ilower + 2
```
