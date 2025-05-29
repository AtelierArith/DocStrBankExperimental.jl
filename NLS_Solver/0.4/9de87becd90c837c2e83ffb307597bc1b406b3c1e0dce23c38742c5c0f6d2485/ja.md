```julia
mutable struct LevenbergMarquardt_BC_Conf <: Abstract_Solver_Conf
    ...
end
```

このコンストラクタを使用します

```julia
LevenbergMarquardt_BC_Conf()
```

境界制約付きレーベンバーグ・マルクワルトソルバーのデフォルト構成パラメータを初期化します。

この方法で問題を解決するには、次に [`solve(nls::AbstractNLS, θ_init::AbstractVector, bc::BoundConstraints, conf::Abstract_BC_Solver_Conf)`](@ref) を呼び出す必要があります。

参照：

  * [`set_max_iteration!(conf::LevenbergMarquardt_BC_Conf,max_iter::Int)`](@ref)
  * [`set_ε_grad_Inf_norm!(conf::LevenbergMarquardt_BC_Conf,ε_grad_Inf_norm::Float64)`](@ref)
  * [`set_ε_step_Inf_norm!(conf::LevenbergMarquardt_BC_Conf,ε_step_Inf_norm::Float64)`](@ref)
