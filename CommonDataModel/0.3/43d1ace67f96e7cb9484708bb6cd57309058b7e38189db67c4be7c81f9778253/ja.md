```
setindex!(d::Dimensions,len,name::AbstractString)
```

`name`という名前の次元を`len`の長さで定義します。例えば：

```julia
ds = NCDataset("file.nc","c")
ds.dim["longitude"] = 100
```

もし`len`が特別な値`Inf`であれば、その次元は`unlimited`と見なされ、NetCDFファイルにデータが追加されるにつれて成長します。
