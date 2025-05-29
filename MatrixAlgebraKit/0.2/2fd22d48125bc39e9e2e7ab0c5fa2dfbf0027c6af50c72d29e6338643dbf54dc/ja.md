```
eig_vals(A; kwargs...) -> D
eig_vals(A, alg::AbstractAlgorithm) -> D
eig_vals!(A, [D]; kwargs...) -> D
eig_vals!(A, [D], alg::AbstractAlgorithm) -> D
```

行列 `A` の固有値のリストを計算します。

!!! note
    バンキングメソッド `eig_vals!` は、出力構造をオプションで受け入れ、入力行列 `A` を破壊する可能性があります。関数の戻り値を常に使用してください。提供された `D` を出力として使用できない場合があるためです。


!!! note
    [`eig_full`](@ref) およびそのバリアントは、入力に追加の構造を仮定しないため、


常に複素数の固有値と固有ベクトルを返します。対称またはエルミート演算子の実固有値分解については、[`eigh_full`](@ref) を参照してください。

また、[`eig_full(!)`](@ref eig_full) および [`eig_trunc(!)`](@ref eig_trunc) も参照してください。
