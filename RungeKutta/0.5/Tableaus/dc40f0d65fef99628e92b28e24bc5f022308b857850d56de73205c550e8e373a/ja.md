Lobatto IIIF̄ タブローは s ステージを持つ

```julia
TableauLobattoIIIF̄(::Type{T}, s)
TableauLobattoIIIF̄(s) = TableauLobattoIIIF̄(Float64, s)
```

コンストラクタは、ステージの数 `s` とオプションでタブローの要素型 `T` を受け取ります。

Lobatto IIIF̄ タブローは [`TableauLobattoIIIF`](@ref) に共役シンプレクティックです。
