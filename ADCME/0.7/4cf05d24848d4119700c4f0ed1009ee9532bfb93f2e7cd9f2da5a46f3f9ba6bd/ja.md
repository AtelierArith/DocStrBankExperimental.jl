```
mpi_sync!(message::Array{Int64,1}, root::Int64 = 0)
mpi_sync!(message::Array{Float64,1}, root::Int64 = 0)
```

すべてのMPIプロセッサ間で`message`を同期します。
