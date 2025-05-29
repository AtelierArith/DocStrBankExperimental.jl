```
residual_order_condition(t::RootedTree, ros::RosenbrockMethod)
```

The residual of the order condition   `(Φ(t) - 1/γ(t)) / σ(t)` with [`elementary_weight`](@ref) `Φ(t)`, [`density`](@ref) `γ(t)`, and [`symmetry`](@ref) `σ(t)` of the [`RosenbrockMethod`](@ref) `ros` for the rooted tree `t`.

# Reference

  * Ernst Hairer, Gerhard Wanner. Solving ordinary differential equations II: Stiff and differential-algebraic problems. Springer, 2010. Section IV.7
