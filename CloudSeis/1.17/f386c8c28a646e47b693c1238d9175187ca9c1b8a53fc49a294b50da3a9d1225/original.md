```
readtrcs!(io::CSeis, trcs, rng...)
```

Read traces from `io` into `trcs::AbstractArray`, and where the size and dimension of `trcs` must correspond to the range specification in `rng...`.

# Example

```julia
container = AzContainer("mydataset-cs"; storageaccount="mystorageaccount")
io = csopen(container)
size(io) # (100,101,102)
trcs = readtrcs!(io, Array{Float32,3}(undef,50,101,1), 1:50, :, 1)
close(io)
```
