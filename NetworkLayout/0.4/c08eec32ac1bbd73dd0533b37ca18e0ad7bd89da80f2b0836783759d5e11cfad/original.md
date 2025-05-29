```
Spring(; kwargs...)(adj_matrix)
spring(adj_matrix; kwargs...)
```

Use the spring/repulsion model of Fruchterman and Reingold (1991, [doi 10.1002/spe.4380211102](https://doi.org/10.1002/spe.4380211102)) with

  * Attractive force:  `f_a(d) =  d^2 / k`
  * Repulsive force:  `f_r(d) = -k^2 / d`

where `d` is distance between two vertices and the optimal distance between vertices `k` is defined as `C * sqrt( area / num_vertices )` where `C` is a parameter we can adjust

Takes adjacency matrix representation of a network and returns coordinates of the nodes.

## Keyword Arguments

  * `dim=2`, `Ptype=Float64`: Determines dimension and output type `Point{dim,Ptype}`.
  * `C=2.0`: Constant to fiddle with density of resulting layout
  * `iterations=100`: maximum number of iterations
  * `initialtemp=2.0`: Initial "temperature", controls movement per iteration
  * `initialpos=Point{dim,Ptype}[]`

    Provide `Vector` or `Dict` of initial positions. All positions will be initialized using random coordinates between [-1,1]. Random positions will be overwritten using the key-val-pairs provided by this argument.
  * `pin=[]`: Pin node positions (won't be updated). Can be given as `Vector` or `Dict`  of node index -> value pairings. Values can be either

      * `(12, 4.0)` : overwrite initial position and pin
      * `true/false` : pin this position
      * `(true, false, false)` : only pin certain coordinates
  * `seed=1`: Seed for random initial positions.
  * `rng=DEFAULT_RNG[](seed)`

    Create rng based on seed. Defaults to `MersenneTwister`, can be specified by overwriting `DEFAULT_RNG[]`
