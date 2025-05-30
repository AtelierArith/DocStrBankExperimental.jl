```julia
derivative_theta(M, theta, beta; scoring_function)

```

モデル `M` のアイテムパラメータ `beta` に対する `theta` のアイテム（カテゴリ）応答関数の導関数を計算します。応答 `y` に対して、原始値と一次導関数を返します。

`y` が省略されると、すべての可能な応答に対する確率と導関数が返されます（[`derivative_theta!`](@ref) も参照）。
