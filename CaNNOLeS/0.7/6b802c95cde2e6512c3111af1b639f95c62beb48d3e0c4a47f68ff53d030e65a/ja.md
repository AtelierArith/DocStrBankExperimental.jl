```
cannoles(nls)
```

非線形制約を持つ非線形最小二乗法のソルバーの実装。

$$
min   f(x) = ¹/₂‖F(x)‖²   s.t.  c(x) = 0
$$

高度な使用法のために、まず `CaNNOLeSSolver` を定義してアルゴリズムで使用するメモリを事前に確保し、その後 `solve!` を呼び出します：

```
solver = CaNNOLeSSolver(nls; linsolve = :ma57)
solve!(solver, nls; kwargs...)
```

または、出力を事前に確保することもできます：

```
stats = GenericExecutionStats(nls)
solve!(solver, nls, stats; kwargs...)
```

# 引数

  * `nls :: AbstractNLSModel{T, V}`: `NLPModels` を使用して作成された非線形最小二乗モデル。

# キーワード引数

  * `x::AbstractVector = nls.meta.x0`: 初期推定値;
  * `λ::AbstractVector = nls.meta.y0`: 初期ラグランジュ乗数;
  * `use_initial_multiplier::Bool = false`: `true` の場合、初期停止テストに `λ` を使用;
  * `method::Symbol = :Newton`: 利用可能なメソッド `:Newton, :LM, :Newton_noFHess`, および `:Newton_vanishing`;
  * `linsolve::Symbol = :ma57`: LDLt因子分解を計算するためのソルバー。利用可能なメソッドは `:ma57`, `:ldlfactorizations`;
  * `max_iter::Int = -1`: 最大反復回数;
  * `max_eval::Real = 100000`: `neval_residual(nls) + neval_cons(nls)` によって計算される最大評価数;
  * `max_time::Float64 = 30.0`: 最大時間制限（秒単位）;
  * `max_inner::Int = 10000`: 最大内部反復回数（この制限に達した場合は停止）;
  * `atol::T = √eps(T)`: 絶対許容誤差;
  * `rtol::T = √eps(T)`: 相対許容誤差: アルゴリズムは `ϵtol := atol + rtol * ‖∇F(x⁰)ᵀF(x⁰) - ∇c(x⁰)ᵀλ⁰‖` を使用;
  * `Fatol::T = √eps(T)`: 残差に対する絶対許容誤差;
  * `Frtol::T = eps(T)`: 残差に対する相対許容誤差、アルゴリズムは ‖F(xᵏ)‖ ≤ Fatol + Frtol * ‖F(x⁰)‖ および ‖c(xᵏ)‖∞ ≤ √ϵtol のときに停止;
  * `verbose::Int = 0`: > 0 の場合、`verbose` 反復ごとに反復の詳細を表示;
  * `always_accept_extrapolation::Bool = false`: `true` の場合、外挿ステップが失敗しても実行;
  * `δdec::Real = T(0.1)`: パラメータ `δ` の減少係数。

アルゴリズムは $‖c(xᵏ)‖∞ ≤ ϵtol$ および $‖∇F(xᵏ)ᵀF(xᵏ) - ∇c(xᵏ)ᵀλᵏ‖ ≤ ϵtol * max(1, ‖λᵏ‖ / 100ncon)$ のときに停止します。

# 出力

返される値は `GenericExecutionStats` です。詳細は `SolverCore.jl` を参照してください。

# コールバック

コールバックは各反復で呼び出されます。コールバックの期待されるシグネチャは `callback(nls, solver, stats)` であり、その出力は無視されます。入力引数のいずれかを変更すると、次の反復に影響を与えます。特に、`stats.status = :user` を設定するとアルゴリズムが停止します。関連情報はすべて `nlp` と `solver` に利用可能です。特に、以下にアクセスし、変更できます：

  * `solver.x`: 現在の反復値;
  * `solver.cx`: `x` における制約の現在の値;
  * `stats`: アルゴリズムの出力を保持する構造体（`GenericExecutionStats`）、これには他の情報が含まれます：

      * `stats.solution`: 現在の反復値;
      * `stats.multipliers`: 制約に対する現在のラグランジュ乗数;
      * `stats.primal_feas`: `solution` におけるプライマル可行性ノルム;
      * `stats.dual_feas`: `solution` におけるデュアル可行性ノルム;
      * `stats.iter`: 現在の反復カウンタ;
      * `stats.objective`: 現在の目的関数の値;
      * `stats.status`: アルゴリズムの現在の状態。アルゴリズムが停止基準に達していない限り `:unknown` であるべきです。これを何かに変更するとアルゴリズムが停止しますが、意図を適切に示すために `:user` を使用するべきです。
      * `stats.elapsed_time`: 経過時間（秒単位）。

# 例

```jldoctest
using CaNNOLeS, ADNLPModels
nls = ADNLSModel(x -> x, ones(3), 3)
stats = cannoles(nls, linsolve = :ldlfactorizations, verbose = 0)
stats

# 出力

"実行統計: 一次の定常状態"
```

```jldoctest
using CaNNOLeS, ADNLPModels
nls = ADNLSModel(x -> x, ones(3), 3)
solver = CaNNOLeSSolver(nls, linsolve = :ldlfactorizations)
stats = solve!(solver, nls, verbose = 0)
stats

# 出力

"実行統計: 一次の定常状態"
```
