```julia
derivative_theta!(
    M,
    probs,
    derivs,
    theta,
    beta;
    scoring_function
)

```

モデル `M` のアイテムパラメータ `beta` に対する `theta` のアイテム（カテゴリ）応答関数の導関数を計算します。この関数は、アイテムカテゴリ応答確率と導関数である `probs` と `derivs` を上書きします。
