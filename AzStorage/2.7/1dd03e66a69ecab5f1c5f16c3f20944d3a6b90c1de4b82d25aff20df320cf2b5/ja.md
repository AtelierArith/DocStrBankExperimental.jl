```
writedlm(io:AzObject, data, args...; options...)
```

配列 `data` を `io::AzObject` に書き込みます。

# 例

```
io = open(AzContainer("mycontainer";storageaccount="mystorageaccount"), "foo.txt")
writedlm(io, rand(10,10))
x = readdlm(io)
```
