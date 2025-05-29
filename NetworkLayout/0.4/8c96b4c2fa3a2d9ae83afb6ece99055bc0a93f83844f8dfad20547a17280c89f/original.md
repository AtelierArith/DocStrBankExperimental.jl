```
SFDP(; kwargs...)(adj_matrix)
sfdp(adj_matrix; kwargs...)
```

Using the Spring-Electric model suggested by Hu (2005, The Mathematica Journal, [pdf](http://yifanhu.net/PUB/graph_draw_small.pdf)).

Forces are calculated as:

```
    f_attr(i,j) = ‖xi - xj‖ ² / K ,    i<->j
    f_repln(i,j) = -CK² / ‖xi - xj‖ ,  i!=j
```

Takes adjacency matrix representation of a network and returns coordinates of the nodes.

## Keyword Arguments

  * `dim=2`, `Ptype=Float64`: Determines dimension and output type `Point{dim,Ptype}`.
  * `tol=1.0`: Stop if position changes of last step `Δp <= tol*K` for all nodes
  * `C=0.2`, `K=1.0`: Parameters to tweak forces.
  * `iterations=100`: maximum number of iterations
  * `initialpos=Point{dim,Ptype}[]`

    Provide `Vector` or `Dict` of initial positions. All positions will be initialized using random coordinates between [-1,1]. Random positions will be overwritten using the key-val-pairs provided by this argument.
  * `pin=[]`: Pin node positions (won't be updated). Can be given as `Vector` or `Dict`  of node index -> value pairings. Values can be either

      * `(12, 4.0)` : overwrite initial position and pin
      * `true/false` : pin this position
      * `(true, false, false)` : only pin certain coordinates
  * `seed=1`: Seed for random initial positions.
  * `rng=DEFAULT_RNG[](seed)`

    Create rng based on seed. Defaults to `MersenneTwister`, can be specified by overwriting `DEFAULT_RNG[]`
