```
solve_model!(m::DBCM)
```

DBCMモデル`m`の尤度を最大化するパラメータを計算します。

# 引数

  * `method::Symbol`: 使用する解法の方法で、`:fixedpoint`（デフォルト）、`:NelderMead`、`:BFGS`、`:LBFGS`、`:Newton`のいずれかを指定できます。
  * `initial::Symbol`: パラメータ$\Theta$の初期推定値で、`:degrees`（デフォルト）、`:degrees*minor`、`:random`、`:uniform`、または`:chung*lu`のいずれかを指定できます。
  * `maxiters::Int`: ソルバーの最大反復回数（デフォルトは1000）。
  * `verbose::Bool`: ログメッセージを表示するかどうかを設定します（デフォルトはfalse）。
  * `ftol::Real`: 固定点法による収束のための関数許容誤差（デフォルトは1e-8）。
  * `abstol::Union{Number, Nothing}`: 他の方法による収束のための絶対関数許容誤差（デフォルトは`nothing`）。
  * `reltol::Union{Number, Nothing}`: 他の方法による収束のための相対関数許容誤差（デフォルトは`nothing`）。
  * `AD_method::Symbol`: 使用する自動微分法で、`:AutoZygote`、`:AutoReverseDiff`、`:AutoForwardDiff`、`:AutoFiniteDiff`のいずれかを指定できます。パフォーマンスは問題のサイズに依存します（デフォルトは`:AutoZygote`）。
  * `analytical_gradient::Bool`: 自動微分で生成されたものの代わりに解析的勾配を使用するかどうかを設定します（デフォルトは`false`）。

# 例

```jldoctest DBCM_solve
# デフォルトの使用
julia> model = DBCM(MaxEntropyGraphs.Graphs.SimpleDiGraph(rhesus_macaques()));

julia> solve_model!(model);

```

```jldoctest DBCM_solve
# 解析的勾配とdegrees minor初期推定を使用
julia> solve_model!(model, method=:BFGS, analytical_gradient=true, initial=:degrees_minor)
(DBCM{Graphs.SimpleGraphs.SimpleDiGraph{Int64}, Float64} (16 vertices, 15 unique degree pairs, 0.94 compression ratio), retcode: Success
u: [3.118482950362848, 2.2567400402511617, 2.2467332710940333, 0.8596258292464105, 0.4957550197436504, 0.3427782029923598, 0.126564995232929, -0.3127732185244699, -0.3967757456352901, -0.43450987676209596  …  -0.5626916621021604, 1.223396713832784, 0.10977479732876981, -1.0367565290851806, -2.0427364999923148, -0.650376357149203, -1.5165614611776657, 0.7532475835319463, 0.39856890694767605, -0.6704522097652438]
最終目的値:     120.15942408828177
)

```
