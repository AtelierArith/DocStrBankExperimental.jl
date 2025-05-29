```
readhdrs!(io::CSeis, hdrs, rng...)
```

`io` から `hdrs::AbstractArray` にトレースヘッダーを読み込み、`hdrs` のサイズと次元は `rng...` の範囲指定に対応する必要があります。 `readtrcs!` とは異なり、各トレースヘッダーの全体を常に読み込みます。したがって、最初の範囲指定子は `:` でなければなりません。

# 例

```julia
container = AzContainer("mydataset-cs"; storageaccount="mystorageaccount")
io = csopen(container)
size(io) # (100,101,102)
hdrs = readhdrs!(io, Array{Float32,3}(undef,headerlength(io),101,1), :, :, 1)
close(io)
```
