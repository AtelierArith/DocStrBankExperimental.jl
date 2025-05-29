```
elementary_weight(t::RootedTree, rk::RungeKuttaMethod)
elementary_weight(t::RootedTree, A::AbstractMatrix, b::AbstractVector, c::AbstractVector)
```

根付き木 `t` に対する [`RungeKuttaMethod`](@ref) `rk` の基本的な重み Φ(`t`) を、バッチャー係数 `A, b, c` を用いて計算します。

参考文献: セクション 312

  * Butcher, John Charles. Numerical methods for ordinary differential equations. John Wiley & Sons, 2008.
