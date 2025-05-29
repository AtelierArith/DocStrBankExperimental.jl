```
resize(v::AbstractSmallVector{N,T}, n::Integer) -> SmallVector{N,T}
```

長さ `n` のベクターを返し、`v` を長くするか短くします。新しいベクターが長くなる場合、新しい要素は `default(T)` で初期化されます。

また、`Base.resize!`、[`SmallCollections.default`](@ref) も参照してください。
