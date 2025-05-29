```
storeimage(format::Symbol, data)
storeimage(file::AbstractString)
```

Stores `data` as `format`. Returns `ImageContainer{format, typeof(data)}`.

# Examples

```julia
c1 = storeimage(:png, read("image.png"))
c2 = storeimage("image.png")
```
