```
schur_full(A; kwargs...) -> T, Z, vals
schur_full(A, alg::AbstractAlgorithm) -> T, Z, vals
schur_full!(A, [TZv]; kwargs...) -> T, Z, vals
schur_full!(A, [TZv], alg::AbstractAlgorithm) -> T, Z, vals
```

正方行列 `A` の完全シュル分解を計算します。ここで、`A * Z = Z * T` となり、直交行列またはユニタリ行列 `Z` にはシュルベクトルが含まれ、正方行列 `T` は上三角（複素数の場合）または準上三角（実数の場合）です。リスト `vals` には、行列 `T` の（準）対角から抽出された `A` の（複素数値の）固有値が含まれます。

!!! note
    バンキングメソッド `schur_full!` は、出力構造をオプションで受け入れ、入力行列 `A` を破壊する可能性があります。関数の戻り値を常に使用してください。提供された `TZv` を出力として使用できない場合があるためです。


```
