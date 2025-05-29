```
readhdrs(io::CSeis, rng...)
```

`io` からトレースヘッダーを読み取ります。 `readtrcs!` とは異なり、各トレースヘッダーの全体を常に読み取ります。したがって、最初の範囲指定子は `:` でなければなりません。

# 例

```julia
container = AzContainer("mydataset-cs"; storageaccount="mystorageaccount")
io = csopen(container)
size(io) # (100,101,102)
hdrs = readhdrs(io, :, :, 1)
close(io)
```
