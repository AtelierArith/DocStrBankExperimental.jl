```
forcecontribution(c::SVector{2, T}, f::SVector{2, T}, δ::SVector{2, T}) where {T}
forcecontribution(c::SVector{3, T}, f::SVector{3, T}, δ::SVector{3, T}) where {T}
```

`c`、`f`、および `δ` の個々のコンポーネントを含む名前付きタプルを返します。

2Dの場合、タプルエントリの名前は `cx`、`cy`、`fx`、`fy` および `δx`、`δy` です。3Dの場合、追加のエントリはそれぞれ `cz`、`fz` および `δz` と呼ばれます。

[`@forcedef`](@ref) を使用した力の蓄積に便利です。
