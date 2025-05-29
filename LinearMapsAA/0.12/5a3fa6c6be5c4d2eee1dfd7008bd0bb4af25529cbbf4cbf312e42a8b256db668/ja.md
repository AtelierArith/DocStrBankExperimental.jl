```
struct LinearMapAX{T,Do,Di,LM,P}
```

`LinearMapAM`と`LinearMapAO`の和集合、なぜならほとんどの操作がAMとAOの両方の型に適用されるからです。

  * `T` : `eltype`
  * `Do` : 出力次元
  * `Di` : 入力次元
  * `LM` : `LinearMap`型
  * `P` : `NamedTuple`型
