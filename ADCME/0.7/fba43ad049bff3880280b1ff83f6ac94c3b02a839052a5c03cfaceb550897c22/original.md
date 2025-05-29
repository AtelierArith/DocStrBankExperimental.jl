```
mpi_halo_exchange2(u::Union{Array{Float64, 2}, PyObject},m::Int64,n::Int64; deps::Union{Missing, PyObject} = missing,
fill_value::Float64 = 0.0, tag::Union{PyObject, Int64} = 0)
```

Similar to [`mpi_halo_exchange`](@ref), but the reach is 2, i.e., for a $N\times N$ matrix $u$, the output will be a  $(N+4)\times (N+4)$ matrix. 
