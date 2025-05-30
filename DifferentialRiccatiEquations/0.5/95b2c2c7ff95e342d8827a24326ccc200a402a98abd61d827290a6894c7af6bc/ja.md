```
Newton(inner_alg; kwargs...)
Newton(; kwargs...)
```

代数リカッティ方程式を解くためのクラインマン-ニュートン法。

```
solve(prob::GAREProblem, Newton(; kwargs...); solve_kwargs...)
```

サポートされているキーワード引数：

  * `inner_alg = ADI()`: 各ニュートンステップで発生する内部リャプノフ方程式を解くためのアルゴリズム
  * `maxiters = 5`: ニュートンステップの最大数
  * `reltol = nothing`: リカッティ残差の相対許容誤差; `nothing`に設定された場合、`size(prob.A, 1) * eps()`に相当
  * `abstol = nothing`: リカッティ残差の絶対許容誤差; `nothing`に設定された場合、`reltol * norm(prob.Q)`（残差がゼロの値）に相当
  * `observer`: [`Callbacks`](@ref)を参照
  * `inexact = true`: （より）不正確なリャプノフ解を許可するかどうか
  * `inexact_forcing = quadratic_forcing`: Dembo et al. (1982)によって説明されたように、強制パラメータ`η = inexact_forcing(i, residual_norm)`を計算します。ここで、`i::Int`はニュートンステップ、`residual_norm::Float64`はリカッティ残差のノルムです。[`quadratic_forcing`](@ref)および[`superlinear_forcing`](@ref)を参照してください。
  * `inexact_hybrid = true`: 古典的ニュートン法の絶対リャプノフ許容誤差が許容誤差`η * residual_norm`よりも厳しくない（すなわち大きい）場合、古典的ニュートン法に切り替えるかどうか。
  * `linesearch = true`: リカッティ残差が十分に減少しなかった場合にArmijoラインサーチを実行するかどうか。例えば、Benner et al. (2015)を参照。

参考文献：

  * Dembo, Eisenstat, Steihaug: Inexact Newton Methods. 1982. https://doi.org/10.1137/0719025
  * Benner, Heinkenschloss, Saak, Weichelt: Inexact low-rank Newton-ADI method for large-scale algebraic Riccati equations. 2015. http://www.mpi-magdeburg.mpg.de/preprints/
