```
const ExactTreewidth{GM} = Treewidth{SafeRules{BT, MMW{3}(), MF}, GM}
ExactTreewidth(; greedy_config = GreedyMethod(nrepeat=1)) = Treewidth(; greedy_config)
```

`ExactTreewidth`は、`BT`除去アルゴリズムを使用した`SafeRules`前処理アルゴリズムのための`Treewidth`の特化版です。`BT`アルゴリズムは、[`TreeWidthSolver.jl`](https://github.com/ArrogantGao/TreeWidthSolver.jl)に実装された木幅問題のための正確なソルバーです。
