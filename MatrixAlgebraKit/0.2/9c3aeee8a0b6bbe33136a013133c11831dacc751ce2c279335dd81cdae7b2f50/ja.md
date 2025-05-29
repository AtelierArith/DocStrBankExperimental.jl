```
svd_compact(A; kwargs...) -> U, S, Vᴴ
svd_compact(A, alg::AbstractAlgorithm) -> U, S, Vᴴ
svd_compact!(A, [USVᴴ]; kwargs...) -> U, S, Vᴴ
svd_compact!(A, [USVᴴ], alg::AbstractAlgorithm) -> U, S, Vᴴ
```

矩形行列 `A` のコンパクト特異値分解 (SVD) を計算します。サイズは `(m, n)` で、`A = U * S * Vᴴ` となります。ここで、`U` はサイズ `(m, k)` の等長行列（直交正規列）であり、`Vᴴ` はサイズ `(k, n)` の直交正規行で構成される行列で、`S` はサイズ `(k, k)` の正方形対角行列です。ここで、`k = min(m, n)` です。

!!! note
    バンキングメソッド `svd_compact!` は、出力構造をオプションで受け入れ、入力行列 `A` を破壊する可能性があります。関数の戻り値を常に使用してください。提供された `USVᴴ` を出力として使用できない場合もあります。


関連情報として [`svd_full(!)`](@ref svd_full)、[`svd_vals(!)`](@ref svd_vals)、および [`svd_trunc(!)`](@ref svd_trunc) を参照してください。
