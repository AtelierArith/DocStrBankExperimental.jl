```
svd_full(A; kwargs...) -> U, S, Vᴴ
svd_full(A, alg::AbstractAlgorithm) -> U, S, Vᴴ
svd_full!(A, [USVᴴ]; kwargs...) -> U, S, Vᴴ
svd_full!(A, [USVᴴ], alg::AbstractAlgorithm) -> U, S, Vᴴ
```

矩形行列 `A` のフル特異値分解 (SVD) を計算します。サイズは `(m, n)` で、`A = U * S * Vᴴ` となります。ここで、`U` と `Vᴴ` はそれぞれサイズ `(m, m)` と `(n, n)` のユニタリ行列であり、`S` はサイズ `(m, n)` の対角行列です。

!!! note
    バンキングメソッド `svd_full!` は、出力構造をオプションで受け入れ、入力行列 `A` を破壊する可能性があります。関数の戻り値を常に使用してください。提供された `USVᴴ` を出力として使用できるとは限りません。


関連情報として [`svd_compact(!)`](@ref svd_compact)、[`svd_vals(!)`](@ref svd_vals)、および [`svd_trunc(!)`](@ref svd_trunc) を参照してください。
