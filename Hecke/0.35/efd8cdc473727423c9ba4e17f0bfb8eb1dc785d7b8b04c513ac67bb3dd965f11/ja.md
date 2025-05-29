```
divisibility(L::ZZLat, v::Union{Vector, QQMatrix}) -> QQFieldElem
```

`v`の`L`に関する可除性を返します。

`L`の周辺二次空間$(V, \Phi)$におけるベクトル`v`に対して、`L`に関する`v`の可除性を、分数$\mathbb Z$-イデアル$\Phi(v, L)$の非負生成元と呼びます。
