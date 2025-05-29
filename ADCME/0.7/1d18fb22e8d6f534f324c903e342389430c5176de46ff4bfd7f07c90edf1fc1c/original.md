```
mpi_recv(a::Union{Array{Float64}, Float64, PyObject}, src::Int64, tag::Int64 = 0)
```

Receives an array from processor `src`. `mpi_recv` requires an input for gradient backpropagation.  Typically we can write

```julia
r = mpi_rank()
a = constant(Float64(r))
if r==1
    a = mpi_send(a, 0)
end
if r==0
    a = mpi_recv(a, 1)
end
```

Then `a=1` on both processor 0 and processor 1.
