```
function partial(data, order, dim, basis; k=autoselect_k(data, basis))
```

`RadialBasisOperator`を構築します。この演算子は、`dim`に関する`order`の偏微分である`Partial`です。
