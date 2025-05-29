```
labelCanonically(Fs::Vector{T})::Vector{T} where {T <: Flag}
```

`Fs`内のすべてのFlagに標準的なラベルを付けます。2つのFlagが同型である場合、この関数は同じFlagを返すべきです。
