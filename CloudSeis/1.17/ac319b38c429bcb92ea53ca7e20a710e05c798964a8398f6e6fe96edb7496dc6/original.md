```
readhdrs!(io::CSeis, hdrs, rng...)
```

Read trace headers from `io` into `hdrs::AbstractArray`, and where the size and dimension of `hdrs` must correspond to the range specification in `rng...`.  Unlike `readtrcs!`, we always read the entirity of each trace header.  Therefore, the first range specifier must be `:`.

# Example

```julia
container = AzContainer("mydataset-cs"; storageaccount="mystorageaccount")
io = csopen(container)
size(io) # (100,101,102)
hdrs = readhdrs!(io, Array{Float32,3}(undef,headerlength(io),101,1), :, :, 1)
close(io)
```
