```
stochastic_block_model(c::Matrix{Float64}, n::Vector{Int}; seed::Int = -1)
stochastic_block_model(cin::Float64, coff::Float64, n::Vector{Int}; seed::Int = -1)
```

Returns a Graph generated according to the Stochastic Block Model (SBM).

`c[a,b]` : Mean number of neighbors of a vertex in block `a` belonging to block `b`.            Only the upper triangular part is considered, since the lower traingular is            determined by $c[b,a] = c[a,b] * n[a]/n[b]$. `n[a]` : Number of vertices in block `a`

The second form samples from a SBM with `c[a,a]=cin`, and `c[a,b]=coff`.

For a dynamic version of the SBM see the `StochasticBlockModel` type and related functions.
