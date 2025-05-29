```
grid_dijkstra(g, s)
```

Apply Dijkstra's algorithm on an `GridGraph` `g`, and return a `ShortestPathTree` with source `s`.

Uses a `DataStructures.BinaryHeap` internally instead of a `DataStructures.PriorityQueue`. Compatible with ForwardDiff.
