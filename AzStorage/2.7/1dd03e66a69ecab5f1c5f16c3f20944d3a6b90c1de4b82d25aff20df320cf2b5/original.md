```
writedlm(io:AzObject, data, args...; options...)
```

write the array `data` to `io::AzObject`

# Example

```
io = open(AzContainer("mycontainer";storageaccount="mystorageaccount"), "foo.txt")
writedlm(io, rand(10,10))
x = readdlm(io)
```
