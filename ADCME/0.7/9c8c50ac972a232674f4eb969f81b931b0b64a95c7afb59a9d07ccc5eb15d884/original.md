```
mpi_send(a::Union{Array{Float64}, Float64, PyObject}, dest::Int64,root::Int64 = 0)
```

Sends `a` to processor `dest`. `a` itself is returned so that the send action can be added to the computational graph.
