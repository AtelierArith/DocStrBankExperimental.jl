```
qr_full(A; kwargs...) -> Q, R
qr_full(A, alg::AbstractAlgorithm) -> Q, R
qr_full!(A, [QR]; kwargs...) -> Q, R
qr_full!(A, [QR], alg::AbstractAlgorithm) -> Q, R
```

矩形行列 `A` の完全な QR 分解を計算します。ここで、`A = Q * R` であり、`Q` は `A` と同じ行数を持つ正方形のユニタリ行列で、`R` は `A` と同じサイズの上三角行列です。

!!! note
    バンキングメソッド `qr_full!` は、出力構造をオプションで受け入れ、入力行列 `A` を破壊する可能性があります。関数の戻り値を常に使用してください。提供された `QR` を出力として使用できない場合があるためです。


関連情報として [`qr_compact(!)`](@ref qr_compact) を参照してください。
