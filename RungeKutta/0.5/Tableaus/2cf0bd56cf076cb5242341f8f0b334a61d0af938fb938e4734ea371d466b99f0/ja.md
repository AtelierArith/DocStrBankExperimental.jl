Lobatto IIIC̄ テーブルは s ステージを持ちます

```julia
TableauLobattoIIIC̄(::Type{T}, s)
TableauLobattoIIIC̄(s) = TableauLobattoIIIC̄(Float64, s)
```

コンストラクタは、ステージの数 `s` とオプションでテーブルの要素型 `T` を受け取ります。

Lobatto IIIC̄ テーブルは [`TableauLobattoIIIC`](@ref) に共役シンプレクティックです。紙の上では、その係数は [`TableauLobattoIII`](@ref) と同じですが、シンプレクティック性の条件によって計算されており、Lobatto III の公式によってではないため、数値的な値はわずかに異なります。
