Lobatto IIIḠ タブローは s ステージを持つ

```julia
TableauLobattoIIIḠ(::Type{T}, s)
TableauLobattoIIIḠ(s) = TableauLobattoIIIḠ(Float64, s)
```

コンストラクタは、ステージの数 `s` とオプションでタブローの要素型 `T` を受け取ります。

Lobatto IIIḠ タブローは [`TableauLobattoIIIG`](@ref) に対して共役シンプレクティックです。紙の上では、Lobatto IIIG タブローの係数はシンプレクティックですが、Lobatto IIIḠ 係数はシンプレクティック性の条件によって計算され、Lobatto IIIG の公式によってではないため、数値的な値はわずかに異なります。
