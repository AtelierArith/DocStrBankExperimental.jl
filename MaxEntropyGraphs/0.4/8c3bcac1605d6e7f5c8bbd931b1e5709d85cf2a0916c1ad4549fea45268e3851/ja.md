```
solve_model!(m::UBCM; kwargs...)
```

UBCMモデル`m`の尤度を最大化するパラメータを計算します。

# 引数

  * `method::Symbol`: 使用する解法の方法で、`:fixedpoint`（デフォルト）、`:NelderMead`、`:BFGS`、`:LBFGS`、`:Newton`のいずれかを指定します。
  * `initial::Symbol`: パラメータ$\Theta$の初期推定値で、`:degrees`、`:degrees*minor`、`:random`、`:uniform`、または`:chung*lu`のいずれかを指定します。
  * `maxiters::Int`: ソルバーの最大反復回数（デフォルトは1000）。
  * `verbose::Bool`: ログメッセージを表示するかどうかを設定します（デフォルトはfalse）。
  * `ftol::Real`: 固定点法による収束のための関数許容誤差（デフォルトは1e-8）。
  * `abstol::Union{Number, Nothing}`: 他の方法による収束のための絶対関数許容誤差（デフォルトは`nothing`）。
  * `reltol::Union{Number, Nothing}`: 他の方法による収束のための相対関数許容誤差（デフォルトは`nothing`）。
  * `AD_method::Symbol`: 使用する自動微分法で、`:AutoZygote`、`:AutoReverseDiff`、`:AutoForwardDiff`、`:AutoFiniteDiff`のいずれかを指定できます。パフォーマンスは問題のサイズに依存します（デフォルトは`:AutoZygote`）。
  * `analytical_gradient::Bool`: 自動微分で生成されたものの代わりに解析的勾配を使用するかどうかを設定します（デフォルトは`false`）。

# 例

```jldoctest UBCM_solve
# デフォルトの使用
julia> model = UBCM(MaxEntropyGraphs.Graphs.SimpleGraphs.smallgraph(:karate));

julia> solve_model!(model);

```

```jldoctest UBCM_solve
# 解析的勾配とdegrees minor初期推定を使用
julia> solve_model!(model, method=:BFGS, analytical_gradient=true, initial=:degrees_minor)
(UBCM{Graphs.SimpleGraphs.SimpleGraph{Int64}, Float64} (34 vertices, 11 unique degrees, 0.32 compression ratio), retcode: Success
u: [2.851659905903854, 2.053008374573552, 1.5432639513870743, 1.152360118212239, 0.8271267490690292, 0.5445045274064909, -0.1398726818076551, -0.3293252270659469, -0.6706207459338859, -1.2685575582149227, -1.410096540372487]
最終目的値:     168.68325136302835
)

```

参照: [`initial_guess`](@ref MaxEntropyGraphs.initial_guess(::UBCM)), [`∇L_UBCM_reduced!`](@ref MaxEntropyGraphs.∇L_UBCM_reduced!)
