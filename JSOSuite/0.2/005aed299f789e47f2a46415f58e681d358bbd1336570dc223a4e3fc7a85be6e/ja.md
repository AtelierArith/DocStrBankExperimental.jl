```
multi_start(nlp::AbstractNLPModel; kwargs...)
```

この関数は、いくつかの初期推測に対してローカル最適化手法を実行するシンプルな最適化戦略を実行します。

# 引数

  * `nlp::AbstractNLPModel{T, V}` は解決すべきモデルを表します。詳細は `NLPModels.jl` を参照してください。

キーワード引数には以下が含まれる場合があります。

  * `multi_solvers::Bool = false`: true の場合、すべての利用可能なソルバーを実行し、そうでない場合は1つのソルバーを実行します;
  * `skip_solvers::Vector{String} = String[]`: `multi_solvers` が true の場合、このリストにあるソルバーはスキップされます;
  * `N::Integer = get_nvar(nlp)`: 考慮される追加の初期推測の数;
  * `max_time::Float64 = 60.0`: 最大時間制限（秒単位）;
  * `verbose::Integer = 0`: > 0 の場合、`verbose` 回の反復ごとに詳細を表示します。
  * `solver_verbose::Integer = 0`: ソルバーの冗長性;
  * `strategy::Symbol = :random`: 次の初期推測を計算するための戦略 [:random] のいずれか。

他のキーワード引数はソルバーに渡されます。
