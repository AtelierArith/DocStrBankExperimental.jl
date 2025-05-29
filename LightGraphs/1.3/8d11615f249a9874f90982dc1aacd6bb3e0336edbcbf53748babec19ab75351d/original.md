```
yen_k_shortest_paths(g, source, target, distmx=weights(g), K=1; maxdist=Inf);
```

Perform [Yen's algorithm](http://en.wikipedia.org/wiki/Yen%27s_algorithm) on a graph, computing k-shortest distances between `source` and `target` other vertices. Return a [`YenState`](@ref) that contains distances and paths.
