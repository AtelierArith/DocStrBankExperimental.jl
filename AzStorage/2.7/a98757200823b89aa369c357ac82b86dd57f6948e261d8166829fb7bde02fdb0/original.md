```
readdlm(io:AzObject, args...; options...)
```

return the parsed delimited blob from the io object `io::AzObject`

# Example

```
io = open(AzContainer("mycontainer";storageaccount="mystorageaccount"), "foo.txt")
data = readdlm(io)
```
