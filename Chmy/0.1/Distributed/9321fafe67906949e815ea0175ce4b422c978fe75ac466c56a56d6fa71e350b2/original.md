```
gather!(dst, src, comm::MPI.Comm; root=0)
```

Gather local array `src` into a global array `dst`. Size of the global array `size(dst)` should be equal to the product of the size of a local array `size(src)` and the dimensions of a Cartesian communicator `comm`. The array will be gathered on the process with id `root` (`root=0` by default). Note that the memory for a global array should be allocated only on the process with id `root`, on other processes `dst` can be set to `nothing`.
