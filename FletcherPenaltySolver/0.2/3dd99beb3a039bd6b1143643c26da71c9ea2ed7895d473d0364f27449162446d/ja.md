```
fps_solve(nlp::AbstractNLPModel{T, S}, x0::S = nlp.meta.x0; subsolver_verbose::Int = 0, kwargs...)
```

Fletcherのペナルティ関数と以下に記載された実装を使用して、境界および等式制約付き最適化問題の局所最小値を計算します。

```
Estrin, R., Friedlander, M. P., Orban, D., & Saunders, M. A. (2020).
Implementing a smooth exact penalty function for equality-constrained nonlinear optimization.
SIAM Journal on Scientific Computing, 42(3), A1809-A1835.
https://doi.org/10.1137/19M1238265
```

高度な使用法では、ソルバーへの主な呼び出しは`NLPStopping`を使用します。詳細は`Stopping.jl`を参照してください。

```
fps_solve(stp::NLPStopping, fpssolver::FPSSSolver{T, QDS, US}; subsolver_verbose::Int = 0)
fps_solve(stp::NLPStopping; subsolver_verbose::Int = 0, kwargs...)
```

# 引数

  * `nlp::AbstractNLPModel`: 解決されるモデル、`NLPModels.jl`を参照してください。
  * `x`: 初期推定値。`x`が指定されていない場合、`nlp.meta.x0`が使用されます。

# キーワード引数

  * `fpssolver`: [`FPSSSolver`](@ref)を参照してください。
  * `verbose::Int = 0`: 0より大きい場合、ソルバーの反復情報を表示します。
  * `subsolver_verbose::Int = 0`: 0より大きい場合、サブソルバーの反復情報を表示します。

停止基準に関するすべての情報は`NLPStopping`オブジェクトで設定できます。追加の`kwargs`は`NLPStopping`に渡されます。デフォルトでは、最適性を宣言するために使用される最適性条件は[`Fletcher_penalty_optimality_check`](@ref)です。

# 出力

返される値は`GenericExecutionStats`で、`SolverCore.jl`を参照してください。

`fps_solve`を呼び出す前に`Stopping`を定義すると、アルゴリズムによって計算されたすべての情報にアクセスできます。

# 注意事項

  * 問題に不等式がある場合、`NLPModelsModifiers.jl`を介して等式と境界のみを取得するためにスラック変数を使用します。
  * `stp.current_state.res`にはFletcherのペナルティ関数の勾配が含まれています。
  * `subproblem_solver`は`NLPStopping`を入力として受け取る必要があります。`StoppingInterface.jl`を参照してください。

# コールバック

コールバックは各反復で呼び出されます。コールバックの期待されるシグネチャは`callback(nlp, solver, stats)`であり、その出力は無視されます。入力引数のいずれかを変更すると、次の反復に影響を与えます。特に、`stats.status = :user`を設定すると、アルゴリズムが停止します。関連するすべての情報は`nlp`と`solver`で利用可能であるべきです。特に、以下にアクセスし、変更できます：

  * `solver`: [`FPSSSolver`](@ref)を参照してください。
  * `stats`: アルゴリズムの出力を保持する構造体（`GenericExecutionStats`）で、他のものの中に以下が含まれます：

      * `stats.dual_feas`: ラグランジアンの現在の勾配のノルム；
      * `stats.primal_feas`: 現在の実現可能性のノルム；
      * `stats.iter`: 現在の反復カウンタ；
      * `stats.objective`: 現在の目的関数の値；
      * `stats.solution`: 現在の反復値；
      * `stats.multipliers`: 現在のラグランジュ乗数の推定；
      * `stats.multipliers_L`および`stats.multipliers_U`: 現在の下限および上限のラグランジュ乗数の推定；
      * `stats.status`: アルゴリズムの現在の状態。アルゴリズムが停止基準に達していない限り、`:unknown`であるべきです。これを何かに変更するとアルゴリズムが停止しますが、意図を適切に示すために`:user`を使用するべきです。
      * `stats.elapsed_time`: 経過時間（秒）。

# 例

```julia
julia> using FletcherPenaltySolver, ADNLPModels
julia> nlp = ADNLPModel(x -> 100 * (x[2] - x[1]^2)^2 + (x[1] - 1)^2, [-1.2; 1.0]);
julia> stats = fps_solve(nlp)
"Execution stats: first-order stationary"
```
