```
const ExactTreewidth{GM} = Treewidth{SafeRules{BT, MMW{3}(), MF}, GM}
ExactTreewidth(; greedy_config = GreedyMethod(nrepeat=1)) = Treewidth(; greedy_config)
```

`ExactTreewidth` is a specialization of `Treewidth` for the `SafeRules` preprocessing algorithm with the `BT` elimination algorithm. The `BT` algorithm is an exact solver for the treewidth problem that implemented in [`TreeWidthSolver.jl`](https://github.com/ArrogantGao/TreeWidthSolver.jl).
