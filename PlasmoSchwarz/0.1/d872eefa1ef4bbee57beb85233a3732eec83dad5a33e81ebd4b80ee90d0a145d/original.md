```
SchwarzAlgorithm(graph::OptiGraph, expanded_subgraphs::Vector{OptiGraph}; kwargs...)
```

Create an algorithm instance by providing the subproblems directly.

```
SchwarzAlgorithm(graph::OptiGraph, partition::Plasmo.Partition; kwargs...)
```

Create an algorithm instance by providing a valid `Plasmo.Partition`.

```
SchwarzAlgorithm(graph::OptiGraph, partition::Plasmo.Partition; kwargs...)
```

Create an algorithm instance and use Metis internally to create partitions.
