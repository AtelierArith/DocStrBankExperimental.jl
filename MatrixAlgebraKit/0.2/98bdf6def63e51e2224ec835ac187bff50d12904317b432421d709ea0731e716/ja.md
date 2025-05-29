```
eigh_vals(A; kwargs...) -> D
eigh_vals(A, alg::AbstractAlgorithm) -> D
eigh_vals!(A, [D]; kwargs...) -> D
eigh_vals!(A, [D], alg::AbstractAlgorithm) -> D
```

対称行列またはエルミート行列 `A` の（実数の）固有値のリストを計算します。

!!! note
    バンキングメソッド `eigh_vals!` は、出力構造をオプションで受け入れ、入力行列 `A` を破壊する可能性があります。関数の戻り値を常に使用してください。提供された `DV` を出力として使用できない場合があるためです。


!!! note
    [`eigh_full`](@ref) およびその変種は、入力に追加の構造を仮定しているため、固有値および固有ベクトルのために入力の `eltype` を保持します。一般的な固有値分解については、[`eig_full`](@ref) を参照してください。


また、[`eigh_full(!)`](@ref eigh_full) および [`eigh_trunc(!)`](@ref eigh_trunc) も参照してください。
