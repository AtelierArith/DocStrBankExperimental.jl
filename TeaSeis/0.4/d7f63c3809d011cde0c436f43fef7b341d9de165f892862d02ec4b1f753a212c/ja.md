```
allocframe(io)
```

JavaSeisデータセットのフレーム用にメモリを割り当てます。 `(Array{Float32,2},Array{UInt8,2})` を返します。例えば、 `trcs, hdrs = allocframe(jsopen("data.js"))`。
