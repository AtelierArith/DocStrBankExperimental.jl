`NLopt.jl`に接続し、最適化バックエンドとして機能します。現在のJuliaセッションで`NLopt.jl`がロードされている場合のみ使用可能です！

# コンストラクタ

```
SemOptimizerNLopt(;
    algorithm = :LD_LBFGS,
    options = Dict{Symbol, Any}(),
    local_algorithm = nothing,
    local_options = Dict{Symbol, Any}(),
    equality_constraints = Vector{NLoptConstraint}(),
    inequality_constraints = Vector{NLoptConstraint}(),
    kwargs...)
```

# 引数

  * `algorithm`: 最適化アルゴリズム。
  * `options::Dict{Symbol, Any}`: 最適化アルゴリズムのオプション
  * `local_algorithm`: ローカル最適化アルゴリズム
  * `local_options::Dict{Symbol, Any}`: ローカル最適化アルゴリズムのオプション
  * `equality_constraints::Vector{NLoptConstraint}`: 等式制約のベクター
  * `inequality_constraints::Vector{NLoptConstraint}`: 不等式制約のベクター

# 例

```julia
my_optimizer = SemOptimizerNLopt()

# 拡張ラグランジュ法による制約付き最適化
my_constrained_optimizer = SemOptimizerNLopt(;
    algorithm = :AUGLAG,
    local_algorithm = :LD_LBFGS,
    local_options = Dict(:ftol_rel => 1e-6),
    inequality_constraints = NLoptConstraint(;f = my_constraint, tol = 0.0),
)
```

# 使用法

NLoptライブラリのすべてのアルゴリズムとオプションが利用可能で、詳細についてはNLopt.jlパッケージおよびNLoptオンラインドキュメントを参照してください。不等式および等式制約の使用方法については、オンラインドキュメントの[制約付き最適化](@ref)を参照してください。

# 拡張ヘルプ

## インターフェース

  * `algorithm(::SemOptimizerNLopt)`
  * `local_algorithm(::SemOptimizerNLopt)`
  * `options(::SemOptimizerNLopt)`
  * `local_options(::SemOptimizerNLopt)`
  * `equality_constraints(::SemOptimizerNLopt)`
  * `inequality_constraints(::SemOptimizerNLopt)`
