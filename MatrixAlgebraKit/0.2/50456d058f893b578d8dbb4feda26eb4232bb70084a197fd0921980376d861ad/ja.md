```
right_polar(A; kwargs...) -> P, Wᴴ
right_polar(A, alg::AbstractAlgorithm) -> P, Wᴴ
right_polar!(A, [PWᴴ]; kwargs...) -> P, Wᴴ
right_polar!(A, [PWᴴ], alg::AbstractAlgorithm) -> P, Wᴴ
```

矩形行列 `A` の完全な極分解を計算します。サイズは `(m, n)` で `n >= m` であり、`A = P * Wᴴ` となります。ここで、`P` はサイズ `(m, m)` の正（半）定値行列であり、`Wᴴ` はサイズ `(n, m)` の直交行列の行を持つ行列（その随伴は等長です）です。

!!! note
    バンキングメソッド `right_polar!` は、出力構造をオプションで受け入れ、入力行列 `A` を破壊する可能性があります。関数の戻り値を常に使用してください。提供された `WP` を出力として使用できない場合があるためです。


他の情報は [`left_polar(!)`](@ref left_polar) を参照してください。 ```
