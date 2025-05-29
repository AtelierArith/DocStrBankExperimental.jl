```
erdos_renyi(GraphType, n, p)
```

Create an [Erdős–Rényi](http://en.wikipedia.org/wiki/Erdős–Rényi_model) random graph with `n` vertices. Edges are added between pairs of vertices with probability `p`.

### Optional Arguments

  * `seed=-1`: set the RNG seed.
  * `rng`: set the RNG directly

### References

  * https://github.com/JuliaGraphs/LightGraphs.jl/blob/2a644c2b15b444e7f32f73021ec276aa9fc8ba30/src/SimpleGraphs/generators/randgraphs.jl
