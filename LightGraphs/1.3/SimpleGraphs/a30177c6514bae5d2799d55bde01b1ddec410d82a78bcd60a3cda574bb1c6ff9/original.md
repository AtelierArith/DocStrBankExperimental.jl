```
random_regular_graph(n, k)
```

Create a random undirected [regular graph](https://en.wikipedia.org/wiki/Regular_graph) with `n` vertices, each with degree `k`.

### Optional Arguments

  * `seed=-1`: set the RNG seed.

### Performance

Time complexity is approximately $\mathcal{O}(nk^2)$.

### Implementation Notes

Allocates an array of `nk` `Int`s, and . For $k > \frac{n}{2}$, generates a graph of degree $n-k-1$ and returns its complement.
