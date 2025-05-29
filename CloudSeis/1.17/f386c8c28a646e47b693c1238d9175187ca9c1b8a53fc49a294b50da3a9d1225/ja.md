```
readtrcs!(io::CSeis, trcs, rng...)
```

`io` から `trcs::AbstractArray` にトレースを読み込み、`trcs` のサイズと次元は `rng...` の範囲指定に対応する必要があります。

# 例

```julia
container = AzContainer("mydataset-cs"; storageaccount="mystorageaccount")
io = csopen(container)
size(io) # (100,101,102)
trcs = readtrcs!(io, Array{Float32,3}(undef,50,101,1), 1:50, :, 1)
close(io)
```
