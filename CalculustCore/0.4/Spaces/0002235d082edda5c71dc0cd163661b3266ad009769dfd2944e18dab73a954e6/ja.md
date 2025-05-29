```
interpOp(V1::AbstractSpace, V2::AbstractSpace)
```

`V1`から`V2`へのグリッド間補間演算子。両方の空間は同じドメインを共有する必要があります。その`[ij]`番目のエントリは、`V2`の`i`番目のグリッドポイントでの`V1`の`j`番目の基底関数の値です。

$$
[J]_{ij} = \phi_{j}(x_i)
$$

`V1 == V2`の場合、単にノーオペレーションの`IdentityOperator(V1)`を返します。
