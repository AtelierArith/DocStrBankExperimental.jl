```
GRASP(;initial, constructor, local_search,...)
```

貪欲ランダム適応探索手法。

# 許可されるパラメータ

  * `initial`: 必要に応じて初期解。
  * `constructor` 貪欲なコンストラクタのためのパラメータ。
  * `local_search` ローカルサーチ戦略 `BestImproveSearch()`（デフォルト）および `FirstImproveSearch()`。

[`GreedyRandomizedConstructor`](@ref)を参照してください。

# 例: ナップサック問題

```julia
import Metaheuristics as MH

# ナップサック問題インスタンスを保存するための型を定義
struct KPInstance
    profit
    weight
    capacity
end

function MH.compute_cost(candidates, constructor, instance::KPInstance)
    # 利益 / 重量の比率
    ratio = instance.profit[candidates] ./ instance.weight[candidates]
    # 非負のコストを最小化することが前提とされている
    maximum(ratio) .- ratio
end

function main()
    # 問題インスタンス
    profit = [55, 10,47, 5, 4, 50, 8, 61, 85, 87]
    weight = [95, 4, 60, 32, 23, 72, 80, 62, 65, 46]
    capacity = 269
    optimum = 295
    instance = KPInstance(profit, weight, capacity)

    # 目的関数と探索空間
    f, search_space, _ = MH.TestProblems.knapsack(profit, weight, capacity)
    candidates = rand(search_space)

    # 各GRASPコンポーネントを定義
    constructor  = MH.GreedyRandomizedConstructor(;candidates, instance, α = 0.95)
    local_search = MH.BestImproveSearch()
    neighborhood = MH.TwoOptNeighborhood()
    grasp = MH.GRASP(;constructor, local_search)
    
    # 最適化し、結果を表示
    result = MH.optimize(f, search_space, grasp)
    display(result)
    # GAPを計算
    fx = -minimum(result)
    GAP = (optimum - fx) / optimum
    println("GAPは ", GAP)
end

main()
```
