```
AlternatingRealTimeHeuristicSearch(
    planners::RealTimeHeuristicSearch...;
    share_values::Bool = true,
    share_search::Bool = false,
    share_paths::Bool = true,
)
```

[`RealTimeHeuristicSearch`](@ref) のバリアント（略して `AlternatingRTHS` または `ARTHS`）で、異なる探索戦略の間で交互に切り替えます。これは1つ以上の `planners` に対応しています。例えば、`ARTHS` は A* 探索を使用する `RTHS` プランナー（`h_mult = 1.0`）と、幅優先探索を使用する `RTHS` プランナー（`h_mult = 0.0`）の間で交互に切り替えることができ、状態空間の更新された領域が深く広いことを保証します。

[`ReusableTreePolicy`](@ref) サブソリューションで構成された [`MultiSolution`](@ref) を返します。デフォルトでは、これらのサブソリューションは同じ価値推定を共有し更新します（`share_values = true`）および目標への最適パスの同じ再利用可能なツリーを共有します（`share_paths = true`）、ただし同じ再利用可能な前方探索ツリーは共有しません（`share_search = false`）。
