```
GMGLinearSolver(
  mh::ModelHierarchy,
  matrices::AbstractArray{<:AbstractMatrix},
  prolongations,
  restrictions;
  pre_smoothers   = Fill(RichardsonSmoother(JacobiLinearSolver(),10),num_levels(mh)-1),
  post_smoothers  = pre_smoothers,
  coarsest_solver = LUSolver(),
  mode::Symbol    = :preconditioner,
  maxiter = 100, atol = 1.0e-14, rtol = 1.0e-08, verbose = false,
)

[`GMGLinearSolverFromMatrices`](@ref)のインスタンスを、基盤となるモデル階層、各レベルのシステム行列、および最も粗いレベルを除く各レベルの転送演算子とスムーザーから作成します。

ソルバーには、kwarg `mode` によって定義される2つの動作モードがあります：

  * `:solver`: GMGソルバーは右辺 `b` を受け取り、解 `x` を返します。
  * `:preconditioner`: GMGソルバーは残差 `r` を受け取り、修正 `dx` を返します。
```
