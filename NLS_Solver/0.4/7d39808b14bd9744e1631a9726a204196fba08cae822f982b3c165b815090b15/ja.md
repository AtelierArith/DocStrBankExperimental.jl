```julia
abstract type Abstract_BC_Solver_Conf end
```

抽象ソルバー設定。これらは境界制約付き非線形最小二乗問題を解くために使用されるソルバーです：

$$
\min\limits_{\theta_l \le \theta \le \theta_u } \frac{1}{2}\|r(\theta)\|^2
$$

実装：

  * [`LevenbergMarquardt_BC_Conf`](@ref)
