```
re, im, w = nyquist(sys[, w])
```

システム `sys` の周波数 `w` における周波数応答の実部と虚部を計算します。詳細は [`nyquistplot`](@ref) を参照してください。

`re` と `im` のサイズは `(ny, nu, length(w))` です。
