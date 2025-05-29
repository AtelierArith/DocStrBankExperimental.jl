```
set!(prop::TraceProperty, hdr::Vector, value)
```

Set the vale of a trace header property for the `hdr`.

# Example

```julia
container = AzContainer("mydataset-cs"; storageaccount="mystorageaccount")
io = csopen(container)
hdrs = readframehdrs(io, 1)
hdr = @view hdrs[:,1]
set!(prop(io, "TRACE"), hdr, 1)
close(io)
```
