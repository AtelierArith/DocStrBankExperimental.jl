```
lq_compact(A; kwargs...) -> L, Q
lq_compact(A, alg::AbstractAlgorithm) -> L, Q
lq_compact!(A, [LQ]; kwargs...) -> L, Q
lq_compact!(A, [LQ], alg::AbstractAlgorithm) -> L, Q
```

矩形行列 `A` のコンパクト LQ 分解を計算します。サイズは `(m,n)` で、`A = L * Q` となります。ここで、サイズ `(min(m,n), n)` の行列 `Q` は、`A'` の像を span する直交行を持ち、サイズ `(m, min(m,n))` の行列 `L` は下三角行列です。

!!! note
    バンキングメソッド `lq_compact!` は、出力構造をオプションで受け入れ、入力行列 `A` を破壊する可能性があります。関数の戻り値を常に使用してください。提供された `LQ` を出力として使用できない場合があります。


!!! note
    コンパクト QR 分解は、`m >= n` の場合に完全 LQ 分解と同等です。一部のアルゴリズムでは `m <= n` が必要な場合があります。


参照してください [`lq_full(!)`](@ref lq_full).
