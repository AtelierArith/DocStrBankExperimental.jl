```
pointwise_dot!(C::VectorData,A::TensorData/VectorData,B::VectorData/TensorData) -> VectorData
```

`A`と`B`の要素ごとのドット積を計算します。`A`は`TensorData`で、`B`は`VectorData`であり、結果を`C`に`VectorData`として返します。
