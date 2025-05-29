```
GMGLinearSolver(
  mh::ModelHierarchy,
  trials::FESpaceHierarchy,
  tests::FESpaceHierarchy,
  biforms::AbstractArray{<:Function},
  interp,
  restrict;
  pre_smoothers   = Fill(RichardsonSmoother(JacobiLinearSolver(),10),num_levels(mh)-1),
  post_smoothers  = pre_smoothers,
  coarsest_solver = Gridap.Algebra.LUSolver(),
  mode::Symbol    = :preconditioner,
  is_nonlinear    = false,
  maxiter = 100, atol = 1.0e-14, rtol = 1.0e-08, verbose = false,
)

[`GMGLinearSolverFromMatrices`](@ref)のインスタンスを、基盤となるモデル階層、試行およびテストFE空間階層、各レベルでの弱形式の左辺、および最も粗いレベルを除く各レベルでの転送演算子とスムーザーから作成します。

ソルバーには、kwarg `mode` によって定義される2つの動作モードがあります：

  * `:solver`: GMGソルバーは右辺 `b` を受け取り、解 `x` を返します。
  * `:preconditioner`: GMGソルバーは残差 `r` を受け取り、修正 `dx` を返します。
```
