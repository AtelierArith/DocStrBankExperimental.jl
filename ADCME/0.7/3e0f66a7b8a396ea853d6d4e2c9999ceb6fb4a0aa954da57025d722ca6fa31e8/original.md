```
mpi_bcast(a::Union{Array{Float64}, Float64, PyObject}, root::Int64 = 0)
```

Broadcast `a` from processor `root` to all other processors.
