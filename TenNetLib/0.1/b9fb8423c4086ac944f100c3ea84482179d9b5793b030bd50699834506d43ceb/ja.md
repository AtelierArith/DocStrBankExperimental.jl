```
function eig_solver(env, phi0::ITensor, time_step::Nothing; kwargs...)
```

"行列" `env` と入力ベクトル `phi0` に対応する最小固有値を見つけるためのソルバーです。

#### `solver` の名前付き引数とそのデフォルト値：

KrylovKit.jl のドキュメントを参照してください。

  * `ishermitian::Bool = true`
  * `solver_tol::Float64 = 1E-14`.
  * `solver_krylovdim::Int = 5`.
  * `solver_maxiter::Int = 2`.
  * `solver_outputlevel::Int = 0`: KrylovKit.jl の `verbosity` を参照してください。
  * `solver_eager::Bool = false`.
  * `solver_check_convergence::Bool = false`.

#### 戻り値：

  * `::Float64`: 最小固有値。
  * `::ITensor`: 最小固有値に対応する固有状態。
