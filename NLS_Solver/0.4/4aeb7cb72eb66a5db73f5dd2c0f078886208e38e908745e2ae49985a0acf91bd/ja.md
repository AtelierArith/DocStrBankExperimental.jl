```julia
abstract type Abstract_Solver_Conf end
```

抽象ソルバー設定。これらは制約のない非線形最小二乗問題を解くために使用されるソルバーです：

$$
\min\limits_\theta \frac{1}{2}\|r(\theta)\|^2
$$

実装：

  * [`LevenbergMarquardt_Conf`](@ref)
