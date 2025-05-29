```
SchwarzAlgorithm(graph::OptiGraph, expanded_subgraphs::Vector{OptiGraph}; kwargs...)
```

サブ問題を直接提供することでアルゴリズムインスタンスを作成します。

```
SchwarzAlgorithm(graph::OptiGraph, partition::Plasmo.Partition; kwargs...)
```

有効な `Plasmo.Partition` を提供することでアルゴリズムインスタンスを作成します。

```
SchwarzAlgorithm(graph::OptiGraph, partition::Plasmo.Partition; kwargs...)
```

アルゴリズムインスタンスを作成し、内部でMetisを使用してパーティションを作成します。
