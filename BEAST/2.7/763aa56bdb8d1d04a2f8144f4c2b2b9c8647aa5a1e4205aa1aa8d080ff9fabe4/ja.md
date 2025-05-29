```
restrict(refspace, element1, element2)
```

`element1`上の局所形状関数のセットの制限を、`element2`上の局所形状関数のセットの線形結合として計算します。より正確には、`restrict`は`NxM`行列`P`を返し、`element2`上の`i`-th局所形状$g_i$関数は次のように書くことができます：

$$
g_i = sum_{j=1}^{M} P_{ij} f_j
$$
