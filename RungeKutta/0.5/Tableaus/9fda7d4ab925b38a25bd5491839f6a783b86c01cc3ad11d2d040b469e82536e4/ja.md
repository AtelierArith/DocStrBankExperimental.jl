Lobatto IIIĀ タブローは s ステージを持つ

```julia
TableauLobattoIIIĀ(::Type{T}, s)
TableauLobattoIIIĀ(s) = TableauLobattoIIIĀ(Float64, s)
```

コンストラクタはステージの数 `s` とオプションでタブローの要素型 `T` を受け取ります。

Lobatto IIIĀ タブローは [`TableauLobattoIIIA`](@ref) の共役シンプレクティックです。紙の上では、その係数は [`TableauLobattoIIIB`](@ref) と同じですが、シンプレクティック性の条件によって計算されており、Lobatto IIIB の公式によってではないため、数値的な値はわずかに異なります。
