```
dense(X::DiscreteState; T = Float32)
```

`X`を適切な密な表現に変換します。`X`が`DiscreteState`の場合、`X`はデフォルトのeltype Float32を持つ`CategoricalLikelihood`に変換されます。`X`が「onehot」`CategoricalLikelihood`の場合、`X`は完全に密なものに変換されます。
