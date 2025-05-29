```
residual_order_condition(t::RootedTree, rk::RungeKuttaMethod)
```

順序条件の残差 `(Φ(t) - 1/γ(t)) / σ(t)` は、[`elementary_weight`](@ref) `Φ(t)`, [`density`](@ref) `γ(t)`, および [`symmetry`](@ref) `σ(t)` の [`RungeKuttaMethod`](@ref) `rk` のブッチャー係数 `A, b, c` に対する根付き木 `t` に関連しています。

参考文献: 

  * Butcher, John Charles. Numerical methods for ordinary differential equations. John Wiley & Sons, 2008.
