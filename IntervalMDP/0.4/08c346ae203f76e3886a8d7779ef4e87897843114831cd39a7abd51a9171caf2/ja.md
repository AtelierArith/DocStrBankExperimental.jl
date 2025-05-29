```
bellman!(workspace, strategy_cache, Vres, V, prob, stateptr; upper_bound = false, maximize = true)
```

値関数 `V` と、値関数 `V` の期待値を上限または下限で制約する区間確率 `prob` を用いて、インプレースでロバストなベルマン更新を計算します。期待値が最大化されるか最小化されるかは、`upper_bound` キーワード引数によって決まります。つまり、`upper_bound == true` の場合は上限が計算され、`upper_bound == false` の場合は下限が計算されます。

出力は入力 `Vres` に構築され、返されます。ワークスペースオブジェクトも変更され、タイプに応じて戦略キャッシュも変更される場合があります。ワークスペースと戦略キャッシュを事前に割り当てる方法の詳細については、[`construct_workspace`](@ref) および [`construct_strategy_cache`](@ref) を参照してください。

### 例

```jldoctest
prob = IntervalProbabilities(;
    lower = sparse_hcat(
        SparseVector(15, [4, 10], [0.1, 0.2]),
        SparseVector(15, [5, 6, 7], [0.5, 0.3, 0.1]),
    ),
    upper = sparse_hcat(
        SparseVector(15, [1, 4, 10], [0.5, 0.6, 0.7]),
        SparseVector(15, [5, 6, 7], [0.7, 0.5, 0.3]),
    ),
)

V = collect(1:15)
workspace = construct_workspace(prob)
strategy_cache = construct_strategy_cache(NoStrategyConfig())
Vres = similar(V)

Vres = bellman!(workspace, strategy_cache, Vres, V, prob; upper_bound = false, maximize = true)
```

[1] M. Lahijanian, S. B. Andersson and C. Belta, "Formal Verification and Synthesis for Discrete-Time Stochastic Systems," in IEEE Transactions on Automatic Control, vol. 60, no. 8, pp. 2031-2045, Aug. 2015, doi: 10.1109/TAC.2015.2398883.
