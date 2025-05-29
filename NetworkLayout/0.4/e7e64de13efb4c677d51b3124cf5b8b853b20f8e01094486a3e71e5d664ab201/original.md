```
Stress(; kwargs...)(adj_matrix)
stress(adj_matrix; kwargs...)
```

Compute graph layout using stress majorization. Takes adjacency matrix representation of a network and returns coordinates of the nodes.

The main equation to solve is (8) in Gansner, Koren and North (2005, [doi 10.1007/978-3-540-31843-9_25](https://doi.org/10.1007/978-3-540-31843-9_25)).

## Inputs:

  * `adj_matrix`: Matrix of pairwise distances.

## Keyword Arguments

  * `dim=2`, `Ptype=Float64`: Determines dimension and output type `Point{dim,Ptype}`.
  * `iterations=:auto`: maximum number of iterations (`:auto` means `400*N^2` where `N` are the number of vertices)
  * `abstols=0`

    Absolute tolerance for convergence of stress. The iterations terminate if the  difference between two successive stresses is less than abstol.
  * `reltols=10e-6`

    Relative tolerance for convergence of stress. The iterations terminate if the difference between two successive stresses relative to the current stress is less than reltol.
  * `abstolx=10e-6`

    Absolute tolerance for convergence of layout. The iterations terminate if the Frobenius norm of two successive layouts is less than abstolx.
  * `weights=Array{Float64}(undef, 0, 0)`

    Matrix of weights. If empty (i.e. not specified), defaults to `weights[i,j] = δ[i,j]^-2` if `δ[i,j]` is nonzero, or `0` otherwise.
  * `initialpos=Point{dim,Ptype}[]`

    Provide `Vector` or `Dict` of initial positions. All positions will be initialized using random coordinates from normal distribution. Random positions will be overwritten using the key-val-pairs provided by this argument.
  * `pin=[]`: Pin node positions (won't be updated). Can be given as `Vector` or `Dict`  of node index -> value pairings. Values can be either

      * `(12, 4.0)` : overwrite initial position and pin
      * `true/false` : pin this position
      * `(true, false, false)` : only pin certain coordinates
  * `seed=1`: Seed for random initial positions.
  * `rng=DEFAULT_RNG[](seed)`

    Create rng based on seed. Defaults to `MersenneTwister`, can be specified by overwriting `DEFAULT_RNG[]`
  * `uncon_dist=(maxdist, Ncomps)->maxdist*Ncomps^(1/3)`

    Per default, unconnected vertices in the graph get a pairwise "ideal" distance which scales with the number of connected components and the maximum distance within the components.
