```
ForwardPlanner(;
    heuristic::Heuristic = GoalCountHeuristic(),
    search_noise::Union{Nothing,Float64} = nothing,
    g_mult::Float32 = 1.0f0,
    h_mult::Float32 = 1.0f0,
    max_nodes::Int = typemax(Int),
    max_time::Float64 = Inf,
    fail_fast::Bool = false,
    refine_method::Symbol = :continue,
    reset_node_count::Bool = true,
    save_search::Bool = true,
    save_search_order::Bool = true,
    save_parents::Bool = false,
    save_children::Bool = false,
    verbose::Bool = false,
    callback = verbose ? LoggerCallback() : nothing
)
```

前方最良探索プランナーで、均一コスト探索、貪欲探索、A*探索を含みます。各ノード $n$ は、優先度 $f(n)$ の増加順に展開されます。$f(n)$ は次のように定義されます：

$$
f(n) = g_\text{mult} \cdot g(n) + h_\text{mult} \cdot h(n)
$$

ここで、$g(n)$ は初期状態から $n$ までの経路コスト、$h(n)$ はヒューリスティックの目標距離推定です。

目標が達成された場合、[`PathSearchSolution`](@ref) を返し、目標ノードに到達するプランを含み、`status` は `:success` に設定されます。ノードまたは時間の予算が尽きた場合、解は代わりに展開のために選択された最後のノードへの部分プランを含み、`status` はそれぞれ `:max_nodes` または `:max_time` に設定されます。

`save_search` が true の場合、返される解はこれまでの探索木とフロンティアを含みます。`save_search` が true で探索空間が枯渇した場合、`status` が `:failure` に設定された `NullSolution` を返します。

# 引数

  * `heuristic`: 状態から目標までのコストを推定する探索ヒューリスティック。
  * `search_noise`: ボルツマン探索ノイズの量（決定論的探索の場合は `nothing`）。
  * `g_mult`: 探索ノードの $f$ 値を計算する際の経路コスト乗数。
  * `h_mult`: 探索ノードの $f$ 値を計算する際のヒューリスティック乗数。
  * `max_nodes`: 終了前の最大探索ノード数。
  * `max_time`: プランナーがタイムアウトする前の最大時間（秒）。
  * `fail_fast`: ヒューリスティックが無限コストを推定した場合に探索を終了するフラグ。
  * `refine_method`: 解の洗練方法（`:continue`、`:reroot`、`:restart` のいずれか）。
  * `reset_node_count`: 解の洗練前に展開されたノード数をリセットするかどうか。
  * `save_search`: 探索木とフロンティアを保存するフラグ（洗練に必要）。
  * `save_search_order`: 解のノード展開順序を保存するフラグ。
  * `save_parents`: 探索木内のすべての親ポインタを保存するフラグ（再根付けに必要）。
  * `save_children`: 探索木内のすべての子ポインタを保存するフラグ（再根付けに必要）。
  * `verbose`: 探索中にデバッグ情報を印刷するフラグ。
  * `callback`: ロギングなどのためのコールバック関数。

# 洗練方法

`refine_method` キーワード引数を設定することで、[`refine!`](@ref) が [`PathSearchSolution`](@ref) に対して呼び出されたときの動作を制御します：

  * `:continue`（デフォルト）：元の開始状態に根ざした探索木を展開することで探索を続けます。この方法が使用される場合、`save_search` はデフォルトで `true` になります。
  * `:reroot`：新しく提供された開始状態で探索木を再根付けし、その後探索を続けます。これはフリンジ取得A* [1] のように行われます。この方法が使用される場合、`save_search`、`save_parents`、および `save_children` はデフォルトで `true` になります。
  * `:restart`：新しい開始状態から探索を再開し、以前の探索木とフロンティアを破棄します。`save_search` が `false` の場合、これは唯一の有効な洗練方法です。

[1] X. Sun, W. Yeoh, and S. Koenig, “Generalized Fringe-Retrieving A*: Faster moving target search on state lattices,” AAMAS (2010), pp. 1081-1088. [https://dl.acm.org/doi/abs/10.5555/1838206.1838352](https://dl.acm.org/doi/abs/10.5555/1838206.1838352)
