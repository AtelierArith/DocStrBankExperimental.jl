```
VNS(;initial, neighborhood_shaking, neighborhood_local, local_search, neighborhood_change)
```

一般的な変分近傍探索。

# 許可されるパラメータ

  * `initial`: 初期解を提供するためにこのパラメータを使用します（オプション）。
  * `neighborhood_shaking`: シェイキングステップのための近傍構造。
  * `neighborhood_local`: ローカルサーチのための近傍構造。
  * `local_search`: ローカルサーチ戦略 `BestImproveSearch()`（デフォルト）および `FirstImproveSearch()`。
  * `neighborhood_change`: 近傍構造間の変更手続き（デフォルト `SequentialChange()`）。

# 例: ナップサック問題

```julia
import Metaheuristics as MH

struct MyKPNeighborhood <: MH.Neighborhood
    k::Int
end

function MH.neighborhood_structure(x, s::MyKPNeighborhood, rng)
    # これはシェイキング手続きがランダムなものを必要とするために定義されています
    # i 番目の隣人ではありません。
    i = rand(rng, 1:length(x))
    reverse!(view(x, i:min(length(x), i+s.k)))
    x
end

function MH.neighborhood_structure(x, s::MyKPNeighborhood, i::Integer)
    # s.k 構造に関して x の周りの i 番目の隣人を返します
    i > length(x) && return nothing
    reverse!(view(x, i:min(length(x), i+s.k)))
    x
end

function main()
    profit = [55, 10,47, 5, 4, 50, 8, 61, 85, 87]
    weight = [95, 4, 60, 32, 23, 72, 80, 62, 65, 46]
    capacity = 269
    nitems = length(weight)

    # 目的関数と探索空間
    f, search_space, _ = MH.TestProblems.knapsack(profit, weight, capacity)

    # 近傍構造のリスト
    neighborhood_shaking = [MyKPNeighborhood(6), MyKPNeighborhood(5), MyKPNeighborhood(4)]
    neighborhood_local = [MyKPNeighborhood(3), MyKPNeighborhood(2), MyKPNeighborhood(1)]
    local_search = MH.BestImproveSearch()
    # VNS をインスタンス化
    vnd = MH.VNS(;neighborhood_shaking, neighborhood_local, local_search, options=MH.Options(verbose=true))

    res = MH.optimize(f, search_space, vnd)
    display(res)
end

main()
```
