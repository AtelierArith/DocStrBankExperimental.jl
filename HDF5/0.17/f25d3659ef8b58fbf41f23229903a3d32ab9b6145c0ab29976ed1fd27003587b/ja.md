```
read_attribute(parent::Union{File,Group,Dataset,Datatype}, name::AbstractString)
```

親オブジェクトの名前付き属性の値を読み取ります。

# 例

```julia-repl
julia> HDF5.read_attribute(g, "time")
2.45
```
