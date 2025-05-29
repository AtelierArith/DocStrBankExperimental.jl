```
Mesh(p::Params; args...)
```

The generated mesh, which includes the degree-of-freedom numbering and all basis functions for the given [`Scenario`](@ref).

This struct contains the following scenario-independent fields:

  * `num1el` –> number of elements in $ζ^1$ direction
  * `num2el` –> number of elements in $ζ^2$ direction
  * `numel` –> number of area elements
  * `num1np` –> number of nodal points in $ζ^1$ direction
  * `num2np` –> number of nodal points in $ζ^2$ direction
  * `numnp` –>  number of nodal points on the 2-d mesh
  * `IX` –> matrix containing nonzero node numbers for each area element
  * `bdry_elems` –> mapping from [`Boundary`](@ref) to element numbers
  * `crnr_elems` –> mapping from [`Corner`](@ref) to element number
  * `bdry_nodes` –> mapping from [`Boundary`](@ref) to node numbers
  * `bdry_inner_nodes` –> mapping from [`Boundary`](@ref) to inner node numbers
  * `crnr_nodes` –> mapping from [`Corner`](@ref) to node number
  * `crnr_inner_nodes` –> mapping from [`Corner`](@ref) to inner node number
  * `kv1` –> [`KnotVector`](@ref) along $ζ^1$ direction
  * `kv2` –> [`KnotVector`](@ref) along $ζ^2$ direction
  * `area_gp_fns` –> [`AreaGpBasisFns`](@ref): 2-D area basis functions
  * `bdry_gp_fns` –> mapping from [`Boundary`](@ref) to [`BdryGpBasisFns`](@ref)
  * `crnr_gp_fns` –> mapping from [`Corner`](@ref) to 2-D basis functions [`GpBasisFnsζα`](@ref)

The generated mesh depends on the problem being solved. The function [`generate_scenario`](@ref MembraneAleFem.generate_scenario) uses the scenario-specific results from `Bc.jl` to set the following scenario-dependent fields:

  * `topology` –> surface [`Topology`](@ref)
  * `dofs` –> list of active [`Unknown`](@ref Dof.Unknown)s with global ordering
  * `ndf` –> number of active [`Unknown`](@ref Dof.Unknown)s
  * `ID` –> matrix mapping node number to indices of unknowns at that node
  * `ID_inv` –> inverse of `ID`: map `unknown_id` to `(node_number, dof_number)`
  * `nmdf` –> total number of mesh degrees of freedom
  * `LM` –> map from area element to indices of all unknowns of that element
  * `inh_dir_bcs` –> list of inhomogeneous Dirichlet boundary conditions
  * `inh_neu_bcs` –> list of inhomogeneous Neumann boundary conditions
