```
readhdrs(io::CSeis, rng...)
```

Read trace headers from `io`.  Unlike `readtrcs!`, we always read the entirity of each trace header.  Therefore, the first range specifier must be `:`.

# Example

```julia
container = AzContainer("mydataset-cs"; storageaccount="mystorageaccount")
io = csopen(container)
size(io) # (100,101,102)
hdrs = readhdrs(io, :, :, 1)
close(io)
```
