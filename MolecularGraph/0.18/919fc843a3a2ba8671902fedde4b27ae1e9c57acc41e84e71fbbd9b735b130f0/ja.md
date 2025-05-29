```
maximum_common_subgraph(g::ConstraintArrayMCES, h::ConstraintArrayMCES;
    connected=false, kwargs...) -> (Dict, Symbol)
```

2つのMCS制約間の最大共通辺誘導部分グラフ（MCES）を計算します。
