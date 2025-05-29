```
System(grid; kwargs...)
```

Create structure of type [`VoronoiFVM.System{Tv,Ti, Tm, TSpecMat<:AbstractMatrix, TSolArray<:AbstractMatrix}`](@ref)  holding data for finite volume system solution. 

Parameters: 

  * `grid::ExtendableGrid`: 1, 2 or 3D computational grid

Keyword arguments:

  * `species`: vector of integer species indices. Added to all grid regions, avoiding the need to call [`enable_species!`](@ref) for this default case.             If it is kept empty, species have be added to the system after creation via  [`enable_species!`](@ref).
  * `unknown_storage`: string or symbol.     Information  on  species  distribution  is kept  in  sparse  or  dense   matrices matrices and, correspondingly, the  solution array is of type   SparseSolutionArray  or matrix,  respectively. In  the case  of sparse   unknown storage,  the system matrix  handles exactly those  degrees of   freedom which correspond to unknowns.  However, handling of the sparse   matrix  structures  for  the   bookkeeping  of  the  unknowns  creates   overhead.

      * `:dense` :  solution vector is an  `nspecies` x `nnodes`  dense matrix
      * `:sparse` :  solution vector is an `nspecies` x `nnodes`  sparse matrix
  * `matrixindextype`: Integer type. Index type for sparse matrices created in the system.
  * `is_linear`: whether the system is linear or not. If it is linear, only one Newton step is used to solve it.
  * `assembly`: either `:cellwise` (default) or `:edgewise`. Determine, how the assembly loop is organized.  `:cellwise` means that the outer loop goes over grid cells (triangles, tetrahedra), and contributions to  edge fluxes and node reactions are calculated for each cell. As a consequence, e.g. im 2D for all interior  edges, flux functions are called twice, once for each adjacent cell. Especially in 3D, this becomes a significant  overhead. With `:edgewise`, geometry factors of these edges are pre-assembled, and the outer assembly loops  go over all grid edges resp. nodes, still with separate calls if neighboring cells belong to different regions.

!!! note
    It is planned to make `:edgewise` the default in a later version.


Physics keyword arguments:

  * `flux`: Function.     Flux between neighboring control volumes: `flux(f,u,edge)` or `flux(f,u,edge,data)`   should return in `f[i]` the flux of species i along the edge joining circumcenters   of neighboring control volumes.  For species i,`u[i,1]` and `u[i,2]` contain the unknown values at the corresponding ends of the edge.
  * `storage`: Function.  Storage term (term under time derivative): `storage(f,u,node)` or `storage(f,u,node,data)`    It should return in `f[i]` the storage term for the i-th equation. `u[i]` contains the value of   the i-th unknown.
  * `reaction`:  Function. Reaction term:  `reaction(f,u,node)` or `reaction(f,u,node,data)`    It should return in `f[i]` the reaction term for the i-th equation. `u[i]` contains the value of   the i-th unknown.
  * `edgereaction`:  Function. Edge reeaction term:  `edgereaction(f,u,edge)` or `edgereaction(f,u,edge,data)`    It should return in `f[i]` the reaction term for the i-th equation.  For species i,`u[i,1]` and `u[i,2]` contain the unknown values at the corresponding ends of the edge.
  * `source`:  Function. Source term: `source(f,node)` or `source(f,node,data)`.   It should return the in `f[i]` the value of the source term for the i-th equation.
  * `bflux`:  Function. Flux between neighboring control volumes on the boundary
  * `breaction` Function.  Boundary reaction term:  `breaction(f,u,node)` or `breaction(f,u,node,data)`    Similar to reaction, but restricted to the inner or outer boundaries.
  * `bcondition` Function. Alias for `breaction`.
  * `bsource`: Function. Boundary source term: `bsource(f,node)` or `bsource(f,node,data)`.   It should return in `f[i]` the value of the source term for the i-th equation.
  * `bstorage`: Function.  Boundary storage term: `bstorage(f,u,node)` or `bstorage(f,u,node,data)`    Similar to storage, but restricted to the inner or outer boundaries.
  * `generic_operator`: Function.  Generic operator  `generic_operator(f,u,sys)`.    This operator acts on the full solution `u` of a system. Sparsity   is detected automatically  unless `generic_operator_sparsity` is given.
  * `generic_operator_sparsity`:  Function defining the sparsity structure of the generic operator.   This should return the sparsity pattern of the `generic_operator`.
  * `nparams`: number of parameters the system is depending on, and with respect to which the derivatives   need to be obtained
  * `data`:  User data (parameters).   This allows to pass various parameters to the callback functions. If `data` is given, all callback functions   should accept a last `data` argument. Otherwise, no data are passed explicitly, and constitutive callbacks can   take parameters from the closure where the function is defined.
  * `matrixtype`: :sparse, :tridiagonal, :banded, :auto. Default: :sparse. :auto leads to automatic choice for dense   solution storage depending on space dimension and number of species.
