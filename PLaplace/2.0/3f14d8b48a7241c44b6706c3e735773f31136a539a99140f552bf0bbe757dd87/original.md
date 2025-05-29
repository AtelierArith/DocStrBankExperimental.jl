```julia
mutable struct PLaplaceData
```

Main output type for solution of a p-Laplace problem. Stores all parameters and results obtained by the solution of a pLaplace problem. Can be used for [Statistics](@ref), [Error Analysis](@ref) and writing the solution to a .vtk-file.

# Fields

  * `mesh::MinFEM.Mesh`: Mesh of computational domain.
  * `dirichlet_nodes::Set{Int64}`: Dirichlet boundary of the computational domain.
  * `fixed_nodes::Union{Missing, Set{Int64}}`: Fixed nodes on the boundary of the computational domain.
  * `neumann_elements::Union{Missing, Set{Int64}}`: Neumann boundary of the computational domain.
  * `f::Union{Missing, AbstractVector{Float64}}`: Domain source term.
  * `h::Union{Missing, AbstractVector{Float64}}`: Neumann boundary condition.
  * `qdim::Int64`: Number of components of the solution.
  * `p::Float64`: PDE parameter.
  * `gradient_bound::Union{Missing, Float64}`: Upper bound for the gradient of the solution.
  * `eps::Float64`: Accuracy of the solution in a variational sense.
  * `stepsize::PLaplace.Stepsize`: Stepping scheme of the interior point method.
  * `Naux::Union{Missing, Int64}`: Number of iterations in the auxilliary path-following.         Is missing if algorithm did not reach auxilliary stage.
  * `Nmain::Union{Missing, Int64}`: Number of iterations for the main path-following         Is missing if algorithm did not reach main stage.
  * `tsetup::Union{Missing, Float64}`: Time required for the setup         Is missing if algorithm did not reach setup stage.
  * `taux::Union{Missing, Float64}`: Time required for the auxilliary path-following         Is missing if algorithm did not reach auxilliary stage.
  * `tmain::Union{Missing, Float64}`: Time required for the main path-following         Is missing if algorithm did not reach main stage.
  * `calculation_nodes::Union{Missing, Set{Int64}}`: Nodes on which the solution was computed, i.e. nodes without Dirichlet condtion.         Is missing if algorithm failed during setup stage.
  * `g::Union{Missing, AbstractVector{Float64}}`: Dirichlet boundary condition prolonged to the whole domain.         Is missing if algorithm failed during setup stage.
  * `u::Union{Missing, AbstractVector{Float64}}`: Shifted solution on calculation nodes without prolonged boundary condition.         Is missing if algorithm did not converge.
  * `v::Union{Missing, AbstractVector{Float64}}`: Solution to the p-Laplace problem.             Is missing if algorithm did not converge.
  * `msg::String`: Notifications from the iteration. In particular contains changes of solvers and         preconditioners and information on early stops.
