```
mpi_send(a::Union{Array{Float64}, Float64, PyObject}, dest::Int64,root::Int64 = 0)
```

`a`をプロセッサ`dest`に送信します。`a`自体が返されるため、送信アクションを計算グラフに追加できます。
