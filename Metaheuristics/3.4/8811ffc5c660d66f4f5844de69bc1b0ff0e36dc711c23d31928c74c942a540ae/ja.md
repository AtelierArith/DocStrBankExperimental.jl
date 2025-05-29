```
VND(;initial, neighborhood, local_search,...)
```

変数近傍降下法。

# 許可されるパラメータ

  * `initial`: 初期解を提供するためにこのパラメータを使用します（オプション）。
  * `neighborhood`: 近傍構造。
  * `local_search` ローカル探索戦略 `BestImproveSearch()`（デフォルト）および `FirstImproveSearch()`。

# 例: ナップサック問題

```julia
import Metaheuristics as MH

struct MyKPNeighborhood <: MH.Neighborhood
    k::Int
end

function MH.neighborhood_structure(x, s::MyKPNeighborhood, i::Integer)
    # s.k 構造に関して x の i 番目の隣接点を返す
    i > length(x) && return nothing
    reverse!(view(x, i:min(length(x), i+s.k)))
    x
end


function main()
    profit = [55, 10,47, 5, 4, 50, 8, 61, 85, 87]
    weight = [95, 4, 60, 32, 23, 72, 80, 62, 65, 46]
    capacity = 269

    # 目的関数と探索空間
    f, search_space, _ = MH.TestProblems.knapsack(profit, weight, capacity)

    # 近傍構造をリストする
    neighborhood = [MyKPNeighborhood(1), MyKPNeighborhood(2), MyKPNeighborhood(3)]
    local_search = MH.BestImproveSearch()
    # VNS をインスタンス化
    vnd = MH.VND(;neighborhood, local_search)

    res = MH.optimize(f, search_space, vnd)
    display(res)
end

main()
```
