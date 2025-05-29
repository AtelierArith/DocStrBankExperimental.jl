```
mpi_sendrecv(a::Union{Array{Float64}, Float64, PyObject}, dest::Int64, src::Int64, tag::Int64=0)
```

`mpi_send` の後に続く `mpi_recv` の便利なラッパーです。
