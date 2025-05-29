```
qr_null(A; kwargs...) -> N
qr_null(A, alg::AbstractAlgorithm) -> N
qr_null!(A, [N]; kwargs...) -> N
qr_null!(A, [N], alg::AbstractAlgorithm) -> N
```

(m, n) 行列 A に対して、A の完全 QR 分解における単位行列 Q 因子の最終的な m - min(m, n) 列に対応する行列 `N` を計算します。すなわち、コンパクト QR 分解の Q 因子に存在しない列です。等長行列 `N` は、A のコケルネルの直交基底をその列として含んでいます。すなわち、`adjoint(A) * N = 0` です。

!!! note
    バンキングメソッド `qr_null!` は、出力構造をオプションで受け入れ、入力行列 A を破壊する可能性があります。関数の戻り値を常に使用してください。提供された `N` 引数を出力として使用できない場合があるためです。


!!! note
    行列 `N` は、m <= n の場合は空です。


他に [`lq_full(!)`](@ref lq_full) および [`lq_compact(!)`](@ref lq_compact) を参照してください。
