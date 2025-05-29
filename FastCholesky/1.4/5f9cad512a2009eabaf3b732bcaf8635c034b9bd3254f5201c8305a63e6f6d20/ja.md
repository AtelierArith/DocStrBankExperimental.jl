```
fastcholesky(input)
```

入力行列 `input` のコレスキー分解を計算します。この関数は、標準の `LinearAlgebra.cholesky` 関数と比較して、特定の入力行列に対してより効率的な実装を提供します。デフォルトでは、`LinearAlgebra.cholesky(PositiveFactorizations.Positive, input)` を使用するため、入力行列が完全に対称である必要はありません。

!!! note
    この関数は、入力行列がほぼ正定値であると仮定しており、行列が正定値になるように最小限の調整を試みます。これらの調整の大きさは必ずしも小さいとは限らないため、入力行列がほぼ正定値であると予想される場合にのみ、この関数を使用することが重要です。


```jldoctest; setup = :(using FastCholesky, LinearAlgebra)
julia> C = fastcholesky([ 1.0 0.5; 0.5 1.0 ]);

julia> C.L * C.L' ≈ [ 1.0 0.5; 0.5 1.0 ]
true
```
