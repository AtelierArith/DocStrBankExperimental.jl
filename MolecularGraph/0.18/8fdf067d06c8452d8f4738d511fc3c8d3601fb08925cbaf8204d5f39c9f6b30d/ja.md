```
maximum_common_subgraph(g::ConstraintArrayMCIS, h::ConstraintArrayMCIS;
    connected=false, kwargs...) -> (Dict, Symbol)
```

2つのMCS制約間の最大共通ノード誘導部分グラフ（MCIS）を計算します。
