```
RealTimeHeuristicSearch(;
    heuristic::Heuristic = GoalCountHeuristic(),
    n_iters::Int = 1,
    max_nodes::Int = 50,
    update_method::Symbol = :dijkstra,
    search_neighbors::Symbol = :unexpanded,
    save_search::Bool = true,
    reuse_search::Bool = false,
    reuse_paths::Bool = true,
    kwargs...
)

RealTimeHeuristicSearch(
    planner::ForwardPlanner,
    n_iters::Int = 1,
    update_method::Symbol = :dijkstra,
    search_neighbors::Symbol = :unexpanded,
    reuse_search::Bool = true,
    reuse_paths::Bool = true,
)
```

リアルタイムヒューリスティックサーチ（`RTHS`）アルゴリズム [1] は `RTDP` に似ています。貪欲なロールアウトの代わりに、現在の状態から前方ヒューリスティックサーチが実行され（最大 `max_nodes` まで）、検索ツリーの内部にあるすべての状態の価値推定が更新されます。`search_neighbors` を設定することで、隣接する状態からも検索を行うことができます。次に、最良の隣接状態に対してシミュレートされたアクションが実行されます。このプロセスは `n_iters` 回繰り返され、将来の検索は更新された価値関数をより情報に基づいたヒューリスティックとして使用します。

[`ReusableTreePolicy`](@ref) を返し、状態価値推定の [`TabularVPolicy`](@ref)、前方検索によって生成された最新の [`PathSearchSolution`](@ref)（`save_search` が `true` の場合は検索ツリーを含む）、および `reuse_paths` が `true` の場合は目標パスの再利用可能なツリーを含みます。

# 引数

  * `planner`: 前方ヒューリスティックサーチに使用される [`ForwardPlanner`](@ref)。[`ForwardPlanner`](@ref) に受け入れられる任意のキーワード引数も `RTHS` のキーワード引数です（例：`heuristic`、`max_nodes`、`save_search` など）。
  * `n_iters`: 実行する反復の数。各反復で、検索の後に最良の隣接状態へのシミュレートされたアクションが続きます。目標または行き止まりに到達した場合、初期状態から再起動します。
  * `update_method`: 価値推定を更新するために使用される方法。端末ノードからのコスト差分（`:costdiff`）またはダイクストラアルゴリズム（`:dijkstra`）を介して行われます。
  * `search_neighbors`: 現在の状態のすべての隣接状態から追加で検索を行うかどうかを制御します（`:all`）、初期検索によって未展開の隣接状態から（`:unexpanded`）、またはそれらのいずれからも行わない（`:none`）。
  * `reuse_search`: `true` の場合、以前の検索ソリューションが将来の反復または [`refine!`](@ref) への呼び出しで再利用されます。後者は `save_search` が `true` である必要があります。検索ソリューションは [`ForwardPlanner`](@ref) の `:reroot` 精緻化方法を介して再利用されます。
  * `reuse_paths`: `true` の場合、目標へのパスが見つかるたびに、それは再利用可能な目標パスのツリーに保存されます。これはツリー適応型 A* [2] のように、将来の検索は以前のパスに遭遇すると終了し、検索コストが削減されます。パスの最適性を確保するために、一貫した `heuristic` が必要です。

# 更新方法

`update_method` キーワード引数を設定することで、価値推定 $V(s)$（または同等に、目標までのコスト推定 $h(s) = -V(s)$）がどのように更新されるかを制御します：

  * `:costdiff`: 価値推定は端末ノード $t$ からのコスト差分によって更新されます。検索ツリーの内部の各ノード $s$ に対して、$s$ から $t$ までのコストの下限を $t$ の目標までのコストに加えることで、目標までのコスト $h(s)$ を推定します：

    $$
    h(s) = h(t) + (c(r, t) - c(r, s))
    $$

    ここで、$c(r, s)$ はルートノード $r$ から $s$ までのコストです。これはリアルタイム適応型 A* [3] によって使用される更新です。これは $O(N)$ 時間を要し、$N$ はツリーの内部のサイズです。
  * `:dijkstra` : 価値推定はダイクストラアルゴリズムを介して検索フロンティアから逆伝播されます。ツリーの内部の各ノード $s$ に対して、フロンティアへのすべてのパスを最小化することで目標までのコスト $h(s)$ を更新します：

    $$
    h(s) = \min_{t \in F} h(t) + c(s, t)
    $$

    これは LSS-LRTA* [4] による更新ルールで、`:costdiff` よりも情報に基づいた価値推定を生成しますが、$O(NB \log NB)$ 時間を要します。$N$ はツリーの内部のサイズ、$B$ は最大分岐係数です。この方法が使用されるとき、[`ForwardPlanner`](@ref) の `save_parents` キーワードはデフォルトで `true` になります。

これらの更新方法の両方は、更新された価値推定が一貫しているために、最初に一貫した `heuristic` を必要とします。

[1] R. E. Korf, "Real-Time Heuristic Search," Artificial Intelligence, vol. 42, no. 2, pp. 189–211, Mar. 1990, [https://doi.org/10.1016/0004-3702(90)90054-4](https://doi.org/10.1016/0004-3702(90)90054-4).

[2] C. Hernández, X. Sun, S. Koenig, and P. Meseguer, "Tree Adaptive A*,"  AAMAS (2011), pp. 123–130. [https://dl.acm.org/doi/abs/10.5555/2030470.2030488](https://dl.acm.org/doi/abs/10.5555/2030470.2030488).

[3] S. Koenig and M. Likhachev, "Real-Time Adaptive A*," AAMAS (2006), pp. 281–288. [https://doi.org/10.1145/1160633.1160682](https://doi.org/10.1145/1160633.1160682).

[4] S. Koenig and X. Sun, "Comparing real-time and incremental heuristic search for real-time situated agents", AAMAS (2009), pp. 313–341. [https://dl.acm.org/doi/10.5555/1018410.1018838](https://dl.acm.org/doi/10.5555/1018410.1018838). ```
