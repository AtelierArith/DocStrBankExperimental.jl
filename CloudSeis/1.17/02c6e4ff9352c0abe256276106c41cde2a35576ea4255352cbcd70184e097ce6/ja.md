```
readtrcs(io::CSeis, trcs, rng...)
```

`rng...` に対して `io` からトレースを読み取ります。

# 例

```julia
container = AzContainer("mydataset-cs"; storageaccount="mystorageaccount")
io = csopen(container)
size(io) # (100,101,102)
trcs = readtrcs(io, 1:50, :, 1)
close(io)
```
