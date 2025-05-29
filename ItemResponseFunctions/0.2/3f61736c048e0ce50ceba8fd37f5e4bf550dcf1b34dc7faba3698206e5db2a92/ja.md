```julia
second_derivative_theta(M, theta, beta; scoring_function)

```

モデル `M` のアイテムパラメータ `beta` に対する `theta` のアイテム（カテゴリ）応答関数の二次導関数を計算します。応答 `y` に対して、原始値、一次導関数、および二次導関数を返します。

`y` が省略された場合、すべての可能な応答に対する原始値と導関数を返します（[`second_derivative_theta!`](@ref) も参照）。
