```julia
second_derivative_theta!(
    M,
    probs,
    derivs,
    derivs2,
    theta,
    beta;
    scoring_function
)

```

モデル `M` のアイテム（カテゴリ）応答関数の `theta` に関する二次導関数を、応答 `y` に対するアイテムパラメータ `beta` を考慮して計算します。原始値、一次導関数、および二次導関数を返します。

`y` が省略された場合、すべての可能な応答に対する値と導関数を返します。

この関数は、それぞれの値で `probs`、`derivs` および `derivs2` を上書きします。
