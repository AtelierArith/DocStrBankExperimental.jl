```
attributes(object::Union{File,Object})
```

ファイルまたはオブジェクトの属性：これは `Attributes` オブジェクトを返します。これは `object` の属性にアクセスするための `Dict` のようなオブジェクトです：`getindex` は [`Attribute`](@ref) オブジェクトを返し、`setindex!` は [`write_attribute`](@ref) を呼び出します。
