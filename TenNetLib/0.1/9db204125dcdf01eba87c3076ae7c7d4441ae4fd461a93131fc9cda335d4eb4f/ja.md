```
function exp_solver(env, phi0::ITensor, time_step::Union{Float64, ComplexF64}; kwargs...)
```

指数化ソルバーは `exp(env * phi0 * time_step)` を見つけるためのものです。

#### `solver` の名前付き引数とそのデフォルト値：

KrylovKit.jl のドキュメントを参照してください。

  * `ishermitian::Bool = true`
  * `solver_tol::Float64 = 1E-12`.
  * `solver_krylovdim::Int = 30`.
  * `solver_maxiter::Int = 10`.
  * `solver_outputlevel::Int = 0`: KrylovKit.jl の `verbosity` を参照してください。
  * `solver_eager::Bool = true`.
  * `solver_check_convergence::Bool = true`.

#### 戻り値：

  * `::Float64`: `NaN`.
  * `::ITensor`: 指数化された `ITensor`。
