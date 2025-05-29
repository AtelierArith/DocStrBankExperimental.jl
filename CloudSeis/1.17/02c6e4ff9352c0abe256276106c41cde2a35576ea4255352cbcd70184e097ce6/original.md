```
readtrcs(io::CSeis, trcs, rng...)
```

Read traces from `io` for the specified `rng...`.

# Example

```julia
container = AzContainer("mydataset-cs"; storageaccount="mystorageaccount")
io = csopen(container)
size(io) # (100,101,102)
trcs = readtrcs(io, 1:50, :, 1)
close(io)
```
