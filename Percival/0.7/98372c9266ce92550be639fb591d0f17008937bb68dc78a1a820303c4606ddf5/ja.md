```
percival(nlp)
```

因子分解を使用しない非線形最適化のための拡張ラグランジュ法。

高度な使用法のためには、まず `PercivalSolver` を定義してアルゴリズムで使用するメモリを事前に確保し、その後 `solve!` を呼び出します：

```
solver = PercivalSolver(nlp)
solve!(solver, nlp)

stats = GenericExecutionStats(nlp)
solver = PercivalSolver(nlp)
solve!(solver, nlp, stats)
```

# 引数

  * `nlp::AbstractNLPModel{T, V}` は解決すべきモデルで、`NLPModels.jl` を参照してください。

# キーワード引数

  * `x::V = nlp.meta.x0`: 初期推定値;
  * `atol::T = T(1e-8)`: 絶対許容誤差;
  * `rtol::T = T(1e-8)`: 相対許容誤差;
  * `ctol::T = atol > 0 ? atol : rtol`: 実現可能性に関する絶対許容誤差;
  * `max_eval::Int = 100000`: 目的関数の評価の最大回数;
  * `max_time::Float64 = 30.0`: 最大時間制限（秒単位）;
  * `max_iter::Int = 2000`: 最大反復回数;
  * `verbose::Int = 0`: > 0 の場合、`verbose` 反復ごとに反復の詳細を表示;
  * `μ::Real = T(10.0)`: ペナルティパラメータの開始値;
  * `η₀::T = T(0.5)`: サブプロブレムの制約許容誤差の開始値;
  * `ω₀::T = T(1)`: サブプロブレムの相対許容誤差の開始値;
  * `ω_min::T = sqrt(eps(T))`: サブプロブレムの相対許容誤差の最小値;
  * `α₁::T = T(9 // 10)`: $η = max(η / al_nlp.μ^α₁, ϵp)$ もし $‖c(xᵏ)‖ ≤ η$ の場合;
  * `β₀::T = T(1)`: `β₁` を参照;
  * `β₁::T = T(1 // 10)`: $η = max(β₀ / al_nlp.μ^β₁, ϵp)$ もし $‖c(xᵏ)‖ > η$ の場合;
  * `μ_up::T = T(10)`: $‖c(xᵏ)‖ > η$ でない場合の `μ` の乗数;
  * `subsolver_logger::AbstractLogger = NullLogger()`: `tron` に渡されるロガー;
  * `subsolver_max_iter = typemax(Int)`: サブソルバーの最大反復回数;
  * `subsolver_max_cgiter = nlp.meta.nvar`: サブソルバーのサブプロブレムの反復制限;
  * `cgls_verbose::Int = 0`: `Krylov.cgls` の冗長性レベル;
  * `inity::Bool = false`: `true` の場合、アルゴリズムは `Krylov.cgls` を使用して近似を計算し、そうでない場合は `nlp.meta.y0` を使用します;

他の `kwargs` はサブプロブレムソルバーに渡されます。

アルゴリズムは $‖c(xᵏ)‖ ≤ ctol$ かつ $‖P∇L(xᵏ,λᵏ)‖ ≤ atol + rtol * ‖P∇L(x⁰,λ⁰)‖$ のときに停止します。ここで $P∇L(x,λ) := Proj_{l,u}(x - ∇f(x) + ∇c(x)ᵀλ) - x$ です。

# 出力

返される値は `GenericExecutionStats` で、`SolverCore.jl` を参照してください。

# コールバック

コールバックは各反復で呼び出されます。コールバックの期待されるシグネチャは `callback(nlp, solver, stats)` で、その出力は無視されます。入力引数のいずれかを変更すると、次の反復に影響を与えます。特に、`stats.status = :user` を設定するとアルゴリズムが停止します。すべての関連情報は `nlp` と `solver` に利用可能であるべきです。特に、以下にアクセスし、変更できます：

  * `solver.x`: 現在の反復値;
  * `solver.gx`: 現在の勾配;
  * `stats`: アルゴリズムの出力を保持する構造体（`GenericExecutionStats`）、その中には他の情報が含まれています：

      * `stats.dual_feas`: ラグランジュの現在の投影勾配のノルム;
      * `stats.primal_feas`: 実現可能性残差のノルム;
      * `stats.iter`: 現在の反復カウンタ;
      * `stats.objective`: 現在の目的関数の値;
      * `stats.multipliers`: 等式制約に関連するラグランジュ乗数の現在の推定値;
      * `stats.status`: アルゴリズムの現在の状態。アルゴリズムが停止基準に達していない限り `:unknown` であるべきです。これを何かに変更するとアルゴリズムが停止しますが、意図を適切に示すために `:user` を使用するべきです。
      * `stats.elapsed_time`: 経過時間（秒単位）。

# 例

```jldoctest
using Percival, ADNLPModels
nlp = ADNLPModel(x -> sum(x.^2), ones(3), x -> [x[1]], zeros(1), zeros(1))
stats = percival(nlp)

# 出力

"Execution stats: first-order stationary"
```

```jldoctest
using Percival, ADNLPModels, SolverCore
nlp = ADNLPModel(x -> sum(x.^2), ones(3), x -> [x[1]], zeros(1), zeros(1))
stats = GenericExecutionStats(nlp)
solver = PercivalSolver(nlp)
stats = solve!(solver, nlp, stats)

# 出力

"Execution stats: first-order stationary"
```
