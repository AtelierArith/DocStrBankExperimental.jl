```
qr_compact(A; kwargs...) -> Q, R
qr_compact(A, alg::AbstractAlgorithm) -> Q, R
qr_compact!(A, [QR]; kwargs...) -> Q, R
qr_compact!(A, [QR], alg::AbstractAlgorithm) -> Q, R
```

矩形行列 `A` のコンパクトQR分解を計算します。サイズは `(m,n)` で、`A = Q * R` となります。ここで、等長行列 `Q` のサイズは `(m, min(m,n))` で、`A` の像を張る直交列を持ち、行列 `R` のサイズは `(min(m,n), n)` で上三角行列です。

!!! note
    バンキングメソッド `qr_compact!` は、出力構造をオプションで受け入れ、入力行列 `A` を破壊する可能性があります。関数の戻り値を常に使用してください。提供された `QR` を出力として使用できない場合があるためです。


!!! note
    コンパクトQR分解は、`m >= n` の場合にフルQR分解と同等です。一部のアルゴリズムは `m >= n` を必要とする場合があります。


参照してください [`qr_full(!)`](@ref qr_full).
