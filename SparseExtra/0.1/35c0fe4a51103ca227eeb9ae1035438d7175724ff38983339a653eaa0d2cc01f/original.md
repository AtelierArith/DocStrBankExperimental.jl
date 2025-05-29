```
dijkstra(distmx::AbstractSparseMatrixCSC, state::DijkstraState, [target]) -> Nothing
```

Given a `distmx` such that `distmx[j, i]` is the distance of the arc i→j and strucutral zeros mean no arc, run the dijkstra algorithm until termination or reaching target (whichever happens first).
