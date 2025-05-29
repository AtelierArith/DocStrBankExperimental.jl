```
storeimage(format::Symbol, data)
storeimage(file::AbstractString)
```

`data`を`format`として保存します。`ImageContainer{format, typeof(data)}`を返します。

# 例

```julia
c1 = storeimage(:png, read("image.png"))
c2 = storeimage("image.png")
```
