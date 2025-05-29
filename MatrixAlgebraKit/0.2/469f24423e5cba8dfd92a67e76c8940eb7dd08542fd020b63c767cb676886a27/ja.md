```
lq_null(A; kwargs...) -> Nᴴ
lq_null(A, alg::AbstractAlgorithm) -> Nᴴ
lq_null!(A, [Nᴴ]; kwargs...) -> Nᴴ
lq_null!(A, [Nᴴ], alg::AbstractAlgorithm) -> Nᴴ
```

(m, n) 行列 A に対して、A の完全 LQ 分解における単位行列 Q 因子の最終的な n - min(m, n) 行に対応する行列 `Nᴴ` を計算します。すなわち、圧縮 LQ 分解の Q 因子に存在しない行です。行列 `Nᴴ` は、等長行列 `N = adjoint(Nᴴ)` が A のカーネル（零空間）の直交基底を列として含むようにします。すなわち、`A * N = 0` または `A * adjoint(Nᴴ) = 0` です。

!!! note
    バンガメソッド `lq_null!` は、出力構造をオプションで受け入れ、入力行列 A を破壊する可能性があります。関数の戻り値を常に使用してください。提供された `Nᴴ` 引数を出力として使用できない場合があるためです。


!!! note
    行列 `Nᴴ` は、`m >= n` の場合は空です。


関連情報として [`qr_full(!)`](@ref lq_full) および [`qr_compact(!)`](@ref lq_compact) を参照してください。
