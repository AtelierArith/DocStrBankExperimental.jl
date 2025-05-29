```
left_polar(A; kwargs...) -> W, P
left_polar(A, alg::AbstractAlgorithm) -> W, P
left_polar!(A, [WP]; kwargs...) -> W, P
left_polar!(A, [WP], alg::AbstractAlgorithm) -> W, P
```

サイズが `(m, n)` の矩形行列 `A` の完全極分解を計算します。ここで `m >= n` であり、`A = W * P` となります。ここで、`W` はサイズが `(m, n)` の等長行列（直交正規列）であり、`P` はサイズが `(n, n)` の正（半）定値行列です。

!!! note
    バンキングメソッド `left_polar!` は、出力構造をオプションで受け入れ、入力行列 `A` を破壊する可能性があります。関数の戻り値を常に使用してください。提供された `WP` を出力として使用できない場合があるためです。


関連情報として [`right_polar(!)`](@ref right_polar) を参照してください。
