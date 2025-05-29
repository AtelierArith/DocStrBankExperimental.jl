```
eigh_full(A; kwargs...) -> D, V
eigh_full(A, alg::AbstractAlgorithm) -> D, V
eigh_full!(A, [DV]; kwargs...) -> D, V
eigh_full!(A, [DV], alg::AbstractAlgorithm) -> D, V
```

対称行列またはエルミート行列 `A` の完全な固有値分解を計算します。これは `A * V = V * D` となるように、単位行列 `V` が直交固有ベクトルを含み、実対角行列 `D` が関連する固有値を含むことを意味します。

!!! note
    バンキングメソッド `eigh_full!` は、出力構造をオプションで受け入れ、入力行列 `A` を破壊する可能性があります。関数の戻り値を常に使用してください。提供された `DV` を出力として使用できない場合があるためです。


!!! note
    [`eigh_full`](@ref) とそのバリエーションは、入力に追加の構造があることを前提としており、


そのため、固有値と固有ベクトルの `eltype` を入力から保持します。一般的な固有値分解については、[`eig_full`](@ref) を参照してください。

また、[`eigh_vals(!)`](@ref eigh_vals) および [`eigh_trunc(!)`](@ref eigh_trunc) も参照してください。
