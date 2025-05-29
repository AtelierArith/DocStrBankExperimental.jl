```
readdlm(io:AzObject, args...; options...)
```

`io::AzObject`から解析された区切り文字のブロブを返します。

# 例

```
io = open(AzContainer("mycontainer";storageaccount="mystorageaccount"), "foo.txt")
data = readdlm(io)
```
