```
stochastic_block_model(c, n)
```

Return a Graph generated according to the Stochastic Block Model (SBM).

`c[a,b]` : Mean number of neighbors of a vertex in block `a` belonging to block `b`.            Only the upper triangular part is considered, since the lower traingular is            determined by $c[b,a] = c[a,b] * \frac{n[a]}{n[b]}$. `n[a]` : Number of vertices in block `a`

### Optional Arguments

  * `seed=-1`: set the RNG seed.

For a dynamic version of the SBM see the [`StochasticBlockModel`](@ref) type and related functions.
