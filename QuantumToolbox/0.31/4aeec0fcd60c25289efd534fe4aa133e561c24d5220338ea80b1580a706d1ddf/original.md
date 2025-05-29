```
eigsolve_al(
    H::Union{AbstractQuantumObject{HOpType},Tuple},
    T::Real,
    c_ops::Union{Nothing,AbstractVector,Tuple} = nothing;
    alg::OrdinaryDiffEqAlgorithm = Tsit5(),
    params::NamedTuple = NamedTuple(),
    ρ0::AbstractMatrix = rand_dm(prod(H.dimensions)).data,
    eigvals::Int = 1,
    krylovdim::Int = min(10, size(H, 1)),
    maxiter::Int = 200,
    eigstol::Real = 1e-6,
    kwargs...,
)
```

Solve the eigenvalue problem for a Liouvillian superoperator `L` using the Arnoldi-Lindblad method.

# Arguments

  * `H`: The Hamiltonian (or directly the Liouvillian) of the system. It can be a [`QuantumObject`](@ref), a [`QuantumObjectEvolution`](@ref), or a tuple of the form supported by [`mesolve`](@ref).
  * `T`: The time at which to evaluate the time evolution.
  * `c_ops`: A vector of collapse operators. Default is `nothing` meaning the system is closed.
  * `alg`: The differential equation solver algorithm. Default is `Tsit5()`.
  * `params`: A `NamedTuple` containing the parameters of the system.
  * `ρ0`: The initial density matrix. If not specified, a random density matrix is used.
  * `eigvals`: The number of eigenvalues to compute.
  * `krylovdim`: The dimension of the Krylov subspace.
  * `maxiter`: The maximum number of iterations for the eigsolver.
  * `eigstol`: The tolerance for the eigsolver.
  * `kwargs`: Additional keyword arguments passed to the differential equation solver.

# Notes

  * For more details about `alg` please refer to [`DifferentialEquations.jl` (ODE Solvers)](https://docs.sciml.ai/DiffEqDocs/stable/solvers/ode_solve/)
  * For more details about `kwargs` please refer to [`DifferentialEquations.jl` (Keyword Arguments)](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/)

# Returns

  * `EigsolveResult`: A struct containing the eigenvalues, the eigenvectors, and some information about the eigsolver

# References

  * [1] Minganti, F., & Huybrechts, D. (2022). Arnoldi-Lindblad time evolution: Faster-than-the-clock algorithm for the spectrum of time-independent and Floquet open quantum systems. Quantum, 6, 649.
