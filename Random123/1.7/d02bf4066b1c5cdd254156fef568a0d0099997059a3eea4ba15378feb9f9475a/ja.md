```julia
Threefry2x{T, R} <: R123Generator2x{T}
Threefry2x([seed, R])
Threefry2x(T[, seed, R])
```

Threefry2xはThreefryカウンターベースのRNGの一種です。2つの数値を同時に生成します。

`T`は`UInt32`または`UInt64`（デフォルト）です。

`seed`は2つの`Integer`の`Tuple`で、両方とも自動的に`T`に変換されます。

`R`はラウンド数を示し、少なくとも1以上32以下でなければなりません。デフォルトで20ラウンドの場合、既知の統計的欠陥がない最小ラウンド数に対してかなりの安全マージンを持っていますが、依然として優れたパフォーマンスを発揮します。
