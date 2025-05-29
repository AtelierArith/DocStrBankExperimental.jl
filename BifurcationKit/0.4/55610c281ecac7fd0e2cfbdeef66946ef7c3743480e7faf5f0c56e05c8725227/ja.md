```julia
mutable struct GMRESIterativeSolvers{T, Tl, Tr} <: BifurcationKit.AbstractIterativeLinearSolver
```

`IterativeSolvers.jl`の`gmres`に基づく線形ソルバー。`(a₀ * I + a₁ * J) * x = rhs`を解くために使用できます。

## フィールド

  * `abstol::Any`: ソルバーの絶対許容誤差 デフォルト: 0.0
  * `reltol::Any`: ソルバーの相対許容誤差 デフォルト: 1.0e-8
  * `restart::Int64`: 再起動の回数 デフォルト: 200
  * `maxiter::Int64`: 最大反復回数 デフォルト: 100
  * `N::Int64`: 問題の次元 デフォルト: 0
  * `verbose::Bool`: 反復中に情報を表示する デフォルト: false
  * `log::Bool`: 情報を記録する デフォルト: true
  * `initially_zero::Bool`: ゼロの推定値から開始する デフォルト: true
  * `Pl::Any`: 左の前処理器 デフォルト: IterativeSolvers.Identity()
  * `Pr::Any`: 右の前処理器 デフォルト: IterativeSolvers.Identity()
  * `ismutating::Bool`: 線形演算子がインプレースで書き込まれるかどうか デフォルト: false
