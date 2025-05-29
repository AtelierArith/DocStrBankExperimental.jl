```
sv, w = sigma(sys[, w])
```

システム `sys` の周波数 `w` における周波数応答の特異値 `sv` を計算します。詳細は [`sigmaplot`](@ref) を参照してください。

`sv` のサイズは `(min(ny, nu), length(w))` です。
