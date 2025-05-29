```
mpi_gather(u::Union{Array{Float64, 1}, PyObject}, deps::Union{Missing, PyObject} = missing)
```

Gathers all the vectors from different processes to the root process. The function returns  a long vector which concatenates of local vectors in the order of process IDs. 
