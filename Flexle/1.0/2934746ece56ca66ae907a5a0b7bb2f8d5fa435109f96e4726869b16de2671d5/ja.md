```
sample(sampler)
```

`sampler`から単一のランダムサンプルを取得し、サンプリングされた要素のインデックスを返します。

逆変換サンプリングによってサンプルを取得します（`cdf_sample`(@ref）を参照）し、`sampler`内の`FlexLevel`を選択し、その`FlexLevel`からインデックスを拒否サンプリングします（`rejection_sample`(@ref）を参照）。
