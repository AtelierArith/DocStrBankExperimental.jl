```
struct Physics
```

Physics data record with the following fields:

  * `flux::Function`: Flux between neighboring control volumes: `flux(f,u,edge,data)` should return in `f[i]` the flux of species i along the edge joining circumcenters of neighboring control volumes.  u is a  2D array such that for species i, `u[i,1]` and `u[i,2]` contain the unknown values at the corresponding ends of the edge.

  * `storage::Function`: Storage term (term under time derivative): `storage(f,u,node,data)`

    It should return in `f[i]` the storage term for the i-th equation. `u[i]` contains the value of the i-th unknown.

  * `reaction::Function`: Reaction term: `reaction(f,u,node,data)`

    It should return in `f[i]` the reaction term for the i-th equation. `u[i]` contains the value of the i-th unknown.

  * `edgereaction::Function`: Edge reaction term: `edgereaction(f,u,edge,data)`

    It should return in `f[i]` the reaction term for the i-th equation. `u[i]` contains the value of the i-th unknown.  u is a  2D array such that for species i, `u[i,1]` and `u[i,2]` contain the unknown values at the corresponding ends of the edge.

  * `source::Function`: Source term: `source(f,node,data)`.

    It should return the in `f[i]` the value of the source term for the i-th equation.

  * `bflux::Function`: Flux between neighboring control volumes on the boundary. Called on edges fully adjacent to the boundary: `bflux(f,u,bedge,data)

  * `breaction::Function`: Boundary reaction term: `breaction(f,u,node,data)` Similar to reaction, but restricted to the inner or outer boundaries.

  * `bsource::Function`: Boundary source term: `bsource(f,node,data)`.

    It should return in `f[i]` the value of the source term for the i-th equation.

  * `bstorage::Function`: Boundary storage term: `bstorage(f,u,node,data)` Similar to storage, but restricted to the inner or outer boundaries.

  * `boutflow::Function`: Outflow boundary term  `boutflow(f,u,edge,data)` This function is called for edges (including interior ones) which have at least one ode on one of the outflow boundaries. Within this function, [`outflownode`](@ref) and  [`isoutflownode`](@ref) can be used to identify that node.  There is some ambiguity in the case that both nodes are outflow nodes, in that case it is assumed that the contribution is zero.

  * `outflowboundaries::Vector{Int64}`: List (Vector) of boundary regions which carry outflow boundary conditions. Influences when `boutflow` is called.

  * `generic_operator::Function`: Generic operator  `generic_operator(f,u,sys)`. This operator acts on the full solution `u` of a system. Sparsity is detected automatically  unless `generic_operator_sparsity` is given.

  * `generic_operator_sparsity::Function`: Function defining the sparsity structure of the generic operator. This should return the sparsity pattern of the `generic_operator`.

  * `data::Any`: User data (parameters). This allows to pass various parameters to the callback functions.

  * `num_species::Int8`: Number of species including boundary species. Meaningless & deprecated.
