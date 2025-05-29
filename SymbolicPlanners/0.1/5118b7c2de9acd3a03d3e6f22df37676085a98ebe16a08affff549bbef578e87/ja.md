```
BackwardPlanner(;
    heuristic::Heuristic = GoalCountHeuristic(:backward),
    search_noise::Union{Nothing,Float64} = nothing,
    g_mult::Float32 = 1.0f0,
    h_mult::Float32 = 1.0f0,
    max_nodes::Int = typemax(Int),
    max_time::Float64 = Inf,
    fail_fast::Bool = false,
    save_search::Bool = false,
    save_search_order::Bool = save_search,
    verbose::Bool = false,
    callback = verbose ? LoggerCallback() : nothing
)
```

ヒューリスティックに基づくバックワード（すなわち回帰）探索プランナー。前方に探索するのではなく、目標から後方に探索し、目標述語を満たす状態の*集合*として扱われる（同等に、*部分*状態として、指定されるのは一部の述語と流動体のみである）。各拡張ノードも部分状態に対応する。[1]

[`ForwardPlanner`](@ref)と同様に、各ノード $n$ は優先度 $f(n)$ の増加順に拡張され、これは次のように定義される：

$$
f(n) = g_\text{mult} \cdot g(n) + h_\text{mult} \cdot h(n)
$$

しかし、$g(n)$ は目標から現在のノード $n$ までの経路コストとして定義され、$h(n)$ は初期状態からの距離のヒューリスティック推定値である。このため、[`GoalCountHeuristic`](@ref) や [`HSPRHeuristic`](@ref) のような特定のヒューリスティックのみがバックワード探索で使用できる。

[`ForwardPlanner`](@ref) と同様に、[`PathSearchSolution`](@ref) または [`NullSolution`](@ref) を返す。

このプランナーは、現在、非ブール流動体を持つドメインや制約仕様を含む問題をサポートしていない。

[1] B. Bonet and H. Geffner, "Planning as Heuristic Search," Artificial Intelligence, vol. 129, no. 1, pp. 5–33, Jun. 2001, [https://doi.org/10.1016/S0004-3702(01)00108-4](https://doi.org/10.1016/S0004-3702(01)00108-4).

# 引数

  * `heuristic`: 状態から目標までのコストを推定する探索ヒューリスティック。
  * `search_noise`: ボルツマン探索ノイズの量（決定論的探索の場合は `nothing`）。
  * `g_mult`: 探索ノードの $f$ 値を計算する際の経路コスト乗数。
  * `h_mult`: 探索ノードの $f$ 値を計算する際のヒューリスティック乗数。
  * `max_nodes`: 終了前の最大探索ノード数。
  * `max_time`: プランナーがタイムアウトする前の最大時間（秒）。
  * `fail_fast`: ヒューリスティックが無限コストを推定した場合に探索を終了するフラグ。
  * `save_search`: 返される解の中で探索木とフロンティアを保存するフラグ。
  * `save_search_order`: 返される解の中でノード拡張順序を保存するフラグ。
  * `verbose`: 探索中にデバッグ情報を印刷するフラグ。
  * `callback`: ロギングなどのためのコールバック関数。
