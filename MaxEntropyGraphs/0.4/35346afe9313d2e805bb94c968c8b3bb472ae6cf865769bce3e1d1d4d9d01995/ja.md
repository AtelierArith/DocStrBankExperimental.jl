```
solve_model!(m::BiCM)
```

BiCMモデル`m`の尤度最大化パラメータを計算します。

# 引数

  * `method::Symbol`: 使用する解法、`:fixedpoint`（デフォルト）、`:NelderMead`、`:BFGS`、`:LBFGS`、`:Newton`のいずれか。
  * `initial::Symbol`: パラメータ$\Theta$の初期推定値、`:degrees`（デフォルト）、`:random`、`:uniform`、または`:chung_lu`のいずれか。
  * `maxiters::Int`: ソルバーの最大反復回数（デフォルトは1000）。
  * `verbose::Bool`: ログメッセージを表示するかどうか（デフォルトはfalse）。
  * `ftol::Real`: fixedpointメソッドによる収束のための関数許容誤差（デフォルトは1e-8）。
  * `abstol::Union{Number, Nothing}`: 他のメソッドによる収束のための絶対関数許容誤差（デフォルトは`nothing`）。
  * `reltol::Union{Number, Nothing}`: 他のメソッドによる収束のための相対関数許容誤差（デフォルトは`nothing`）。
  * `AD_method::Symbol`: 使用する自動微分メソッド、`:AutoZygote`、`:AutoReverseDiff`、`:AutoForwardDiff`、`:AutoFiniteDiff`のいずれか。パフォーマンスは問題のサイズに依存します（デフォルトは`:AutoZygote`）。
  * `analytical_gradient::Bool`: 自動微分で生成されたものの代わりに解析的勾配を使用するかどうか（デフォルトは`false`）。

# 例

```jldoctest BiCM_solve
# デフォルトの使用
julia> model = BiCM(corporateclub());

julia> solve_model!(model);

```

```jldoctest BiCM_solve
# 解析的勾配と均一な初期推定を使用
julia> solve_model!(model, method=:BFGS, analytical_gradient=true, initial=:uniform)
(BiCM{Graphs.SimpleGraphs.SimpleGraph{Int64}, Float64} (25 + 15 vertices, 6 + 6 unique degrees, 0.30 compression ratio), retcode: Success
u: [1.449571644621672, 0.8231752829683303, 0.34755085972479766, -0.04834480708852856, -0.3984299800917503, -0.7223268299919358, 1.6090554004279671, 1.2614196476197532, 0.9762560461922147, 0.11406188481061938, -0.24499004480426345, -2.2646067641037333]
最終目的値:     171.15095803718134
)

```
