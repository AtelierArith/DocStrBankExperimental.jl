```
set!(prop::TraceProperty, hdrs::Matrix, i, value)
```

`hdrs`のi列目のヘッダープロパティの値を設定します。

# 例

```julia
container = AzContainer("mydataset-cs"; storageaccount="mystorageaccount")
io = csopen(container)
hdrs = readframehdrs(io, 1)
set!(prop(io, "TRACE"), hdr, 1, 2)
close(io)
```
