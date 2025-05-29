```
residual_order_condition(t::RootedTree, ros::RosenbrockMethod)
```

順序条件の残差 `(Φ(t) - 1/γ(t)) / σ(t)` は、根付き木 `t` に対する [`RosenbrockMethod`](@ref) `ros` の [`elementary_weight`](@ref) `Φ(t)`, [`density`](@ref) `γ(t)`, および [`symmetry`](@ref) `σ(t)` を用いて計算されます。

# 参考文献

  * Ernst Hairer, Gerhard Wanner. Solving ordinary differential equations II: Stiff and differential-algebraic problems. Springer, 2010. Section IV.7
