```
indim(c::VertexModel)::Int
indim(c::EdgeModel)::@NamedTuple{src::Int,dst::Int}
```

[`hasinsym`](@ref)/[`hasindim`](@ref) が true を返した *後* に呼び出す必要があります。入力次元を返します。
