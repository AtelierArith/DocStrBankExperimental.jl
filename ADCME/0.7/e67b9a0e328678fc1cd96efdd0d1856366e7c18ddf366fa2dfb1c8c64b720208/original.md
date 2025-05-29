```
mpi_halo_exchange(u::Union{Array{Float64, 2}, PyObject},m::Int64,n::Int64; deps::Union{Missing, PyObject} = missing,
fill_value::Float64 = 0.0, tag::Union{PyObject, Int64} = 0)
```

Perform Halo exchnage on `u` (a $k \times k$ matrix). The output has a shape $(k+2)\times (k+2)$

  * `fill_value`: value used for the boundaries
  * `tag`: message tag
  * `deps`: a **scalar** tensor; it can be used to serialize the MPI calls
