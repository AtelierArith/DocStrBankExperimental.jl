```
solve_plaplace(
    p::Float64,
    mesh::Mesh,
    g::Union{AbstractVector{Float64}, Function},
    dirichlet_boundary::Set{Boundary};
    <keyword arguments>
) -> PLaplaceData
```

Returns solution to a given problem for the p-Laplace operator with a Dirichlet condition on (a part of) the boundary. Additionally, a volume source term and Neumann conditions on a non-intersecting part of the boudary can be specified. The solution is computed by an interior-point method applied to a reformulated problem. For more information on the algorithm, please look at the [algorithm](@ref algorithm-theory) page of the documentation.

Below you find a list of mandatory and keyword arguments indicating which functions can be specified continously or discrete and which parameters can be adjusted. Further, the outputs can be controlled in particular if log and vtk files are generated. It is also possible to track the condition number of the system matrix during the iteration, but please not that this significantly impacts the performance and requires a lot of memory. 

# Mandatory Arguments

  * `p::Float64`: problem parameter.
  * `mesh::Mesh`: FEM mesh of the domain.
  * `g::Union{AbstractVector{Float64}, Function}`: Dirichlet boundary condition.
  * `dirichlet_boundary::Union{Set{Boundary}, Set{Int64}}`: Parts of the physical boundary to   hold the Dirichlet condition. Either given by set of named boundaries or node ids.

# Keyword Arguments

  * `f::Union{AbstractVector{Float64}, Function, Missing} = missing`:   Discrete or continous source term.
  * `neumann_boundary::Union{Set{Boundary}, Set{Int64}, Missing} = missing`:   Parts of the physical boundary to hold Neumann condition.   Either given by set of named boundaries or boundary element ids.
  * `h::Union{AbstractVector{Float64}, Function, Missing} = missing`:   Discrete or continous Neumann boundary condition. Requires `neumann_boundary` to be set.
  * `boundary_prolongation::Union{AbstractVector{Float64}, Missing} = missing`:   Prescribed discrete prolongation of the Dirichlet condition to the full domain.   Will be computed during the algorithm if not set.
  * `fixed_nodes::Union{Set{Boundary}, Set{Int64}, Missing} = missing,`:   Set of fixed node indices, i.e. additional homogeneous Dirichlet nodes.   Either given by set of named boundaries or node ids.   Is ignored if `boundary_prolongation` is set.
  * `qdim::Int64 = 1`:   Number of components of the problem, respectively f, g and h as well as u and v.   Is mandatory to set for vector-valued setting.
  * `eps::Float64 = 1e-6`:   Accuracy of the solution.   In particular termination criterion for the main path-following.
  * `stepsize::Stepsize = ADAPTIVE`:   Specifier for using an alternative stepping scheme in the internal path-following.
  * `maxiterations::Int64 = 1000`:   Maximal number of iteriations per stage of the internal path-following schemes.
  * `kappa::Float64 = 10.0`:   Parameter used for updates of the step length in long-step path-following variants.
  * `backtracking_maxiterations::Int64 = 25`:    Maximal number of iterations in backtracking search for the update of the iterate   in long-step path-following variants.
  * `backtracking_decrementfactor::Float64 = 0.25`:   Decrement factor in backtracking search of long-step path-following variants.
  * `solver::LinearSolver = CHOLESKY`:   Specifier for the solver internally used for linear systems.
  * `preconditioner::Preconditioner = NONE`:   Specifier for the preconditioner internally used for linear systems.
  * `useharmonicprolongation::Bool = true`:   Flag for prolongation of boundary condition as solution to the harmonic problem or by 0.   Is ignored if `boundary_prolongation` is set.
  * `vtkfile::Union{String,Missing} = missing`:   File name for writing solution to vtk. If not set, no file will be written.
  * `verbose::Bool = true`:   Flag if log is written to console during the iteration.
  * `logfile::Union{String,Missing} = missing`:   File name for writing log to a file. If not set, log will not be exported.
  * `logcondition::Bool = false`:   Flag for tracking condition of the system matrix is tracked and included in log file.   Will only be exported if `logfile` is set.
