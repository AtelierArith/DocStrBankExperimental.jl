```
enumerate_paths(state[, vs])
```

Given a path state `state` of type `AbstractPathState`, return a vector (indexed by vertex) of the paths between the source vertex used to compute the path state and a single destination vertex, a list of destination vertices, or the entire graph. For multiple destination vertices, each path is represented by a vector of vertices on the path between the source and the destination. Nonexistent paths will be indicated by an empty vector. For single destinations, the path is represented by a single vector of vertices, and will be length 0 if the path does not exist.

### Implementation Notes

For Floyd-Warshall path states, please note that the output is a bit different, since this algorithm calculates all shortest paths for all pairs of vertices: `enumerate_paths(state)` will return a vector (indexed by source vertex) of vectors (indexed by destination vertex) of paths. `enumerate_paths(state, v)` will return a vector (indexed by destination vertex) of paths from source `v` to all other vertices. In addition, `enumerate_paths(state, v, d)` will return a vector representing the path from vertex `v` to vertex `d`.
