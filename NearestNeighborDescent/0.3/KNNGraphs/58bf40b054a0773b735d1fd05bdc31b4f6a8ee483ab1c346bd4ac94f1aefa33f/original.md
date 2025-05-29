ApproximateKNNGraph{V, U, D, M} subtypes are weighted, directed graphs where each vertex has exactly `k` forward edges with weights of type `U`.

`D` is the type of the dataset corresponding to this graph, and `M` is a `Distances.PreMetric` with result type matching `U`.
