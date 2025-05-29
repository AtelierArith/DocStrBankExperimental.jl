```
mpi_sum(a::Union{Array{Float64}, Float64, PyObject}, root::Int64 = 0)
```

MPIプロセッサ`root`上で`a`を合計します。
