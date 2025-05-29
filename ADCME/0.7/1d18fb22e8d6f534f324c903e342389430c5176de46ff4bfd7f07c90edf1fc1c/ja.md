```
mpi_recv(a::Union{Array{Float64}, Float64, PyObject}, src::Int64, tag::Int64 = 0)
```

プロセッサ `src` から配列を受信します。 `mpi_recv` は勾配逆伝播のための入力を必要とします。 通常、次のように記述できます。

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

これにより、プロセッサ 0 とプロセッサ 1 の両方で `a=1` になります。
