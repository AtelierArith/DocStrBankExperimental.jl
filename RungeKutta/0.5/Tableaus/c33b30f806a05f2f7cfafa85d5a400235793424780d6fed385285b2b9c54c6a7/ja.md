Lobatto IIIB̄ テーブルは s ステージを持ちます

```julia
TableauLobattoIIIB̄(::Type{T}, s)
TableauLobattoIIIB̄(s) = TableauLobattoIIIB̄(Float64, s)
```

コンストラクタは、ステージの数 `s` とオプションでテーブルの要素型 `T` を受け取ります。

Lobatto IIIB̄ テーブルは [`TableauLobattoIIIB`](@ref) に対して共役シンプレクティックです。紙の上では、その係数は [`TableauLobattoIIIA`](@ref) と同じですが、シンプレクティック性の条件によって計算されており、Lobatto IIIA の公式によってではないため、数値的な値はわずかに異なります。
