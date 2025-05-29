```
CartesianTopology(comm, dims)
```

Create an N-dimensional Cartesian topology using base MPI communicator `comm` with dimensions `dims`. If all entries in `dims` are not equal to `0`, the product of `dims` should be equal to the total number of MPI processes `MPI.Comm_size(comm)`. If any (or all) entries of `dims` are `0`, the dimensions in the corresponding spatial directions will be picked automatically.
