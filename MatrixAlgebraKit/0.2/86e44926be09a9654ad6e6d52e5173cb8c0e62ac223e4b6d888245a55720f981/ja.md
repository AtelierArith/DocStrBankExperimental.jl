```
eig_full(A; kwargs...) -> D, V
eig_full(A, alg::AbstractAlgorithm) -> D, V
eig_full!(A, [DV]; kwargs...) -> D, V
eig_full!(A, [DV], alg::AbstractAlgorithm) -> D, V
```

正方行列 `A` の完全な固有値分解を計算します。ここで、`A * V = V * D` となり、可逆行列 `V` には固有ベクトルが含まれ、対角行列 `D` には関連する固有値が含まれます。

!!! note
    バンキングメソッド `eig_full!` は、出力構造をオプションで受け入れ、入力行列 `A` を破壊する可能性があります。関数の戻り値を常に使用してください。提供された `DV` を出力として使用できない場合があるためです。


!!! note
    [`eig_full`](@ref) とそのバリアントは、入力に追加の構造を仮定しないため、


常に複素数の固有値と固有ベクトルを返します。対称またはエルミート演算子の実固有値分解については、[`eigh_full`](@ref) を参照してください。

また、[`eig_vals(!)`](@ref eig_vals) および [`eig_trunc(!)`](@ref eig_trunc) も参照してください。
