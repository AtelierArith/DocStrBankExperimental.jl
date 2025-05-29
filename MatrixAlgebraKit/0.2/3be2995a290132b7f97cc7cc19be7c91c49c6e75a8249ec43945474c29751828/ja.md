```
schur_vals(A; kwargs...) -> vals
schur_vals(A, alg::AbstractAlgorithm) -> vals
schur_vals!(A, [vals]; kwargs...) -> vals
schur_vals!(A, [vals], alg::AbstractAlgorithm) -> vals
```

行列 `A` のシュール分解を計算することによって、`A` の固有値のリストを計算します。

!!! note
    バンキングメソッド `schur_vals!` は、出力構造をオプションで受け入れ、入力行列 `A` を破壊する可能性があります。関数の戻り値を常に使用してください。提供された `vals` を出力として使用できない場合があるためです。


[`eig_full(!)`](@ref eig_full) と [`eig_trunc(!)`](@ref eig_trunc) も参照してください。
