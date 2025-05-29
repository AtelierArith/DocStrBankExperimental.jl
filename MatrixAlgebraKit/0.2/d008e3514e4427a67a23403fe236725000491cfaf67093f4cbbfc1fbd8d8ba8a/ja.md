```
lq_full(A; kwargs...) -> L, Q
lq_full(A, alg::AbstractAlgorithm) -> L, Q
lq_full!(A, [LQ]; kwargs...) -> L, Q
lq_full!(A, [LQ], alg::AbstractAlgorithm) -> L, Q
```

矩形行列 `A` の完全な LQ 分解を計算します。ここで、`A = L * Q` であり、`Q` は `A` と同じ行数を持つ正方形のユニタリ行列で、`L` は `A` と同じサイズの下三角行列です。

!!! note
    バンキングメソッド `lq_full!` は、出力構造をオプションで受け入れ、入力行列 `A` を破壊する可能性があります。関数の戻り値を常に使用してください。提供された `LQ` を出力として使用できない場合があるためです。


関連情報として [`lq_compact(!)`](@ref lq_compact) を参照してください。
