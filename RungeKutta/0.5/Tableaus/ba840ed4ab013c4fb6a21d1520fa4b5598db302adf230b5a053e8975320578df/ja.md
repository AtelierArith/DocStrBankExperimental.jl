Lobatto IIID̄ テーブルは s ステージを持ちます

```julia
TableauLobattoIIID̄(::Type{T}, s)
TableauLobattoIIID̄(s) = TableauLobattoIIID̄(Float64, s)
```

コンストラクタは、ステージの数 `s` とオプションでテーブルの要素型 `T` を受け取ります。

Lobatto IIID̄ テーブルは [`TableauLobattoIIID`](@ref) に対して共役シンプレクティックです。紙の上では、Lobatto IIID テーブルの係数はシンプレクティックですが、Lobatto IIID̄ 係数はシンプレクティック性条件によって計算され、Lobatto IIID の公式によってではないため、数値的な値はわずかに異なります。
