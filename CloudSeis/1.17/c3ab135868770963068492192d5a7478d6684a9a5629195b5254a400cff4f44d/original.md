```
set!(prop::TraceProperty, hdrs::Matrix, i, value)
```

Set the vale of the header property for the ith column of `hdrs`.

# Example

```julia
container = AzContainer("mydataset-cs"; storageaccount="mystorageaccount")
io = csopen(container)
hdrs = readframehdrs(io, 1)
set!(prop(io, "TRACE"), hdr, 1, 2)
close(io)
```
