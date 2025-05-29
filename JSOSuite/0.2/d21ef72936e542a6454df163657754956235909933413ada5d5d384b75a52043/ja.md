```
stats = minimize(nlp::Union{AbstractNLPModel, JuMP.Model}; kwargs...)
```

最適化問題 `nlp` の局所最小値を計算します。

```
stats = minimize(f::Function, x0::AbstractVector, args...; kwargs...)
stats = minimize(F::Function, x0::AbstractVector, nequ::Integer, args...; kwargs...)
```

[`ADNLPModel`](https://juliasmoothoptimizers.github.io/ADNLPModels.jl/stable/) を使用して NLPModel を定義します。

```
stats = minimize(c, H, c0 = c0, x0 = x0, name = name; kwargs...)
stats = minimize(c, H, lvar, uvar, c0 = c0, x0 = x0, name = name; kwargs...)
stats = minimize(c, H, A, lcon, ucon, c0 = c0, x0 = x0, name = name; kwargs...)
stats = minimize(c, H, lvar, uvar, A, lcon, ucon, c0 = c0, x0 = x0, name = name; kwargs...)
```

[`QuadraticModel`](https://juliasmoothoptimizers.github.io/QuadraticModels.jl/stable/) を使用して QuadraticModel を定義します。

オプティマイザは次のように選択できます。

```
stats = minimize(optimizer_name::String, args...; kwargs...)
```

`JuMP.Model` は NLPModelsJuMP.jl を介して NLPModels に変換されます。

最適化問題が二次または線形の目的関数と線形制約を持つ場合は、モデル定義に QuadraticModels.jl または LLSModels.jl を使用することを検討してください。

# キーワード引数

すべてのキーワード引数は選択したソルバーに渡されます。すべてのソルバーで利用可能なキーワードは以下の通りです：

  * `atol`: 絶対許容誤差；
  * `rtol`: 相対許容誤差；
  * `max_time`: 最大秒数；
  * `max_iter`: 最大反復回数；
  * `max_eval`: 最大の制約 + 目的評価数；
  * `callback = (args...) -> nothing`: 各反復で呼び出されるコールバック；
  * `verbose::Int = 0`: 0より大きい場合、`verbose` 反復ごとに反復の詳細を表示します。

以下は非線形最小二乗に特有のものです：

  * `Fatol::T = √eps(T)`: 残差に対する絶対許容誤差；
  * `Frtol::T = eps(T)`: 残差に対する相対許容誤差。アルゴリズムは ‖F(xᵏ)‖ ≤ Fatol + Frtol * ‖F(x⁰)‖ のときに停止します。

さらなる可能なオプションは各ソルバーのドキュメントに記載されています。

## コールバック

コールバックは各反復で呼び出されます。コールバックの期待されるシグネチャは `callback(nlp, solver, stats)` であり、その出力は無視されます。入力引数のいずれかを変更すると、次の反復に影響を与えます。特に、`stats.status = :user` を設定するとアルゴリズムが停止します。関連情報はすべて `nlp` と `solver` に利用可能であるべきです。

# 出力

返される値は `GenericExecutionStats` です。詳細は `SolverCore.jl` を参照してください。

# 例

```jldoctest; output = false
using JSOSuite
stats = minimize(x -> 100 * (x[2] - x[1]^2)^2 + (x[1] - 1)^2, [-1.2; 1.0], verbose = 0)
stats

# output

"Execution stats: first-order stationary"
```

利用可能なソルバーのリストは `JSOSuite.optimizers[!, :name]` を使用して取得するか、[`select_optimizers`](@ref) を参照してください。

```jldoctest; output = false
using JSOSuite
stats = minimize("TRON", x -> 100 * (x[2] - x[1]^2)^2 + (x[1] - 1)^2, [-1.2; 1.0], verbose = 0)
stats

# output

"Execution stats: first-order stationary"
```

一部のオプティマイザは、読み込み後のみ利用可能です。

```jldoctest; output = false
using JSOSuite
# ここでは境界制約のある二次問題を最小化します
c = [1.0; 1.0]
H = [-2.0 0.0; 3.0 4.0]
uvar = [1.0; 1.0]
lvar = [0.0; 0.0]
x0 = [0.5; 0.5]
stats = minimize("TRON", c, H, lvar, uvar, x0 = x0, name = "bndqp_QP", verbose = 0)
stats

# output

"Execution stats: first-order stationary"

```
