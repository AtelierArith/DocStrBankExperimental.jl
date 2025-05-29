```
svd_trunc(A; kwargs...) -> U, S, Vᴴ
svd_trunc(A, alg::AbstractAlgorithm) -> U, S, Vᴴ
svd_trunc!(A, [USVᴴ]; kwargs...) -> U, S, Vᴴ
svd_trunc!(A, [USVᴴ], alg::AbstractAlgorithm) -> U, S, Vᴴ
```

行列 `A` の部分的または切り捨てられた特異値分解 (SVD) を計算します。ここで、`A * (Vᴴ)' = U * S` となります。ここで、`U` はサイズ `(m, k)` の等長行列（直交正規列）であり、`Vᴴ` はサイズ `(k, n)` の直交正規行で構成される行列で、`S` はサイズ `(k, k)` の正方形対角行列であり、`k` は切り捨て戦略によって設定されます。

!!! note
    バンキングメソッド `svd_trunc!` は、出力構造をオプションで受け入れ、入力行列 `A` を破壊する可能性があります。関数の戻り値を常に使用してください。提供された `USVᴴ` を出力として使用できない場合があるためです。


他に [`svd_full(!)`](@ref svd_full)、[`svd_compact(!)`](@ref svd_compact)、および [`svd_vals(!)`](@ref svd_vals) を参照してください。
