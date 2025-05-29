```julia
Threefry4x{T, R} <: R123Generator4x{T}
Threefry4x([seed, R])
Threefry4x(T[, seed, R])
```

Threefry2xは、ThreefryカウンターベースのRNGの一種です。一度に4つの数値を生成します。

`T`は`UInt32`または`UInt64`（デフォルト）です。

`seed`は4つの`Integer`の`Tuple`で、すべて自動的に`T`に変換されます。

`R`はラウンドを示し、少なくとも1以上32以下でなければなりません。デフォルトで20ラウンドの場合、既知の統計的欠陥がない最小ラウンド数に対してかなりの安全マージンがありますが、依然として優れたパフォーマンスを持っています。
