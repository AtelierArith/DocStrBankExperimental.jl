Lobatto IIIĒ タブローは s ステージを持つ

```julia
TableauLobattoIIIĒ(::Type{T}, s)
TableauLobattoIIIĒ(s) = TableauLobattoIIIĒ(Float64, s)
```

コンストラクタは、ステージの数 `s` とオプションでタブローの要素型 `T` を受け取ります。

Lobatto IIIĒ タブローは [`TableauLobattoIIIE`](@ref) に対して共役シンプレクティックです。紙の上では、Lobatto IIIE タブローの係数はシンプレクティックですが、Lobatto IIIĒ 係数はシンプレクティシティ条件によって計算され、Lobatto IIIE の公式によってではないため、数値的な値はわずかに異なります。
