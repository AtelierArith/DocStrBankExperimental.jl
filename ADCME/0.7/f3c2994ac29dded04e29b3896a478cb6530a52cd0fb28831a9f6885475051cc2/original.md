```
mpi_sendrecv(a::Union{Array{Float64}, Float64, PyObject}, dest::Int64, src::Int64, tag::Int64=0)
```

A convenient wrapper for `mpi_send` followed by `mpi_recv`.
