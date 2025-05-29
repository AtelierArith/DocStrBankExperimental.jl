```
marginalise(D::AbstractDistribution, K::AbstractMarkovKernel)
```

Dに関するKの周辺化Mを計算します。すなわち、

M(y) = ∫ K(y,x)D(x) dx
