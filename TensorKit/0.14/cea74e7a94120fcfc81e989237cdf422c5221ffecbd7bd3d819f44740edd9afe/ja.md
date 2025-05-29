```
⊗(t1::AbstractTensorMap, t2::AbstractTensorMap, ...) -> TensorMap
otimes(t1::AbstractTensorMap, t2::AbstractTensorMap, ...) -> TensorMap
```

2つの`AbstractTensorMap`インスタンス間のテンソル積を計算します。これにより、新しい`TensorMap`インスタンスが生成され、そのコドメインは`codomain(t1) ⊗ codomain(t2)`であり、ドメインは`domain(t1) ⊗ domain(t2)`です。
