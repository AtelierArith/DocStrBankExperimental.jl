```
derivative_weight(t::RootedTree, rk::RungeKuttaMethod)
```

ルート付き木 `t` に対するバーチャー係数 `A, b, c` を持つ [`RungeKuttaMethod`](@ref) `rk` の導関数重み (ΦᵢD)(`t`) を計算します。

参考文献: 

  * Butcher, John Charles. Numerical methods for ordinary differential equations. John Wiley & Sons, 2008.
