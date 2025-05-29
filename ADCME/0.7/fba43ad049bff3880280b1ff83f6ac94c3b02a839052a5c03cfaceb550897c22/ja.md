```
mpi_halo_exchange2(u::Union{Array{Float64, 2}, PyObject},m::Int64,n::Int64; deps::Union{Missing, PyObject} = missing,
fill_value::Float64 = 0.0, tag::Union{PyObject, Int64} = 0)
```

[`mpi_halo_exchange`](@ref)と同様ですが、範囲は2です。つまり、$N\times N$行列$u$の場合、出力は$(N+4)\times (N+4)$行列になります。
