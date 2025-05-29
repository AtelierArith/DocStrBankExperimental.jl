```
mpi_bcast(a::Union{Array{Float64}, Float64, PyObject}, root::Int64 = 0)
```

プロセッサ `root` からすべての他のプロセッサに `a` をブロードキャストします。
