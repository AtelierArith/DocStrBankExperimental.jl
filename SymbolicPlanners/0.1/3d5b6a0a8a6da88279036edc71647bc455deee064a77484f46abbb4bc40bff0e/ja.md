```
BreadthFirstPlanner(;
    max_nodes::Int = typemax(Int),
    max_time::Float64 = Inf,
    save_search::Bool = false,
    save_search_order::Bool = save_search,
    verbose::Bool = false,
    callback = verbose ? LoggerCallback() : nothing
)
```

幅優先探索プランナー。ノードは初期状態からの距離が増加する順に展開され（以前に訪れたノードはスキップされる）、

[`PathSearchSolution`](@ref) または [`NullSolution`](@ref) を返します。これは [`ForwardPlanner`](@ref) に似ています。

# 引数

  * `max_nodes`: 終了前の最大探索ノード数。
  * `max_time`: プランナーがタイムアウトする前の最大時間（秒）。
  * `save_search`: 返される解に探索ツリーとフロンティアを保存するフラグ。
  * `save_search_order`: 返される解にノード展開順を保存するフラグ。
  * `verbose`: 探索中にデバッグ情報を印刷するフラグ。
  * `callback`: ロギングなどのためのコールバック関数。
