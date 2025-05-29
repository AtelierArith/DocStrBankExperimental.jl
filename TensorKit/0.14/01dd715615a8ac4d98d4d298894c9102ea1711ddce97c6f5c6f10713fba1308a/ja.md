```
InnerProductStyle(V::VectorSpace) -> ::InnerProductStyle
InnerProductStyle(S::Type{<:VectorSpace}) -> ::InnerProductStyle
```

ベクトル空間の内積の型を返します。これは次のいずれかです。

  * `NoInnerProduct()`: `dual(V)` から `conj(V)` への写像がない、すなわちメトリックがない
  * `HasInnerProduct` のサブタイプ: メトリックは存在するが、さらなるサポートは実装されていない
  * `EuclideanInnerProduct()`: メトリックは恒等であり、双対空間と共役空間が同型である。
