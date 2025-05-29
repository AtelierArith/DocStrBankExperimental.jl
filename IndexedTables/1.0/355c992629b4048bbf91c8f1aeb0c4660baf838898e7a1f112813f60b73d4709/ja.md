```
pkeynames(t::NDSparse)
```

`t`の主キー列の名前。

# 例

```
x = ndsparse([1,2],[3,4])
pkeynames(x)

x = ndsparse((x=1:10, y=1:2:20), rand(10))
pkeynames(x)
```
