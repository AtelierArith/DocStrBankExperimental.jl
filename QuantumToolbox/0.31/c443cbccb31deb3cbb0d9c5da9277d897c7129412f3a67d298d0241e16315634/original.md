```
eigsolve(A::QuantumObject; 
    v0::Union{Nothing,AbstractVector}=nothing, 
    sigma::Union{Nothing, Real}=nothing,
    eigvals::Int = 1,
    krylovdim::Int = max(20, 2*k+1),
    tol::Real = 1e-8,
    maxiter::Int = 200,
    solver::Union{Nothing, SciMLLinearSolveAlgorithm} = nothing,
    kwargs...)
```

Solve for the eigenvalues and eigenvectors of a matrix `A` using the Arnoldi method.

# Arguments

  * `A::QuantumObject`: the [`QuantumObject`](@ref) to solve eigenvalues and eigenvectors.
  * `v0::Union{Nothing,AbstractVector}`: the initial vector for the Arnoldi method. Default is a random vector.
  * `sigma::Union{Nothing, Real}`: the shift for the eigenvalue problem. Default is `nothing`.
  * `eigvals::Int`: the number of eigenvalues to compute. Default is `1`.
  * `krylovdim::Int`: the dimension of the Krylov subspace. Default is `max(20, 2*k+1)`.
  * `tol::Real`: the tolerance for the Arnoldi method. Default is `1e-8`.
  * `maxiter::Int`: the maximum number of iterations for the Arnoldi method. Default is `200`.
  * `solver::Union{Nothing, SciMLLinearSolveAlgorithm}`: the linear solver algorithm. Default is `nothing`.
  * `kwargs`: Additional keyword arguments passed to the solver.

# Notes

  * For more details about `solver` and extra `kwargs`, please refer to [`LinearSolve.jl`](https://docs.sciml.ai/LinearSolve/stable/)

# Returns

  * `EigsolveResult`: A struct containing the eigenvalues, the eigenvectors, and some information about the eigsolver
