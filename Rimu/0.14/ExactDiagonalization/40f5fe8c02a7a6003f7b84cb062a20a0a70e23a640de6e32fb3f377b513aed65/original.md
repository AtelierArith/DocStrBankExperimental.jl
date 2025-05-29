The module `Rimu.ExactDiagonalization` provides a framework for exact diagonalization of quantum many-body systems defined by an [`AbstractHamiltonian`](@ref) type.

The main usage is through defining an [`ExactDiagonalizationProblem`](@ref) and solving it with the [`solve`](@ref solve(::ExactDiagonalizationProblem)) function. The module provides a unified interface for accessing different solver algorithms, which make use of solvers provided by external packages.

## Exports

  * [`ExactDiagonalizationProblem`](@ref)
  * [`BasisSetRepresentation`](@ref)
  * [`build_basis`](@ref)
  * [`KrylovKitSolver`](@ref)
  * [`LinearAlgebraSolver`](@ref)
  * [`ArpackSolver`](@ref)
  * [`LOBPCGSolver`](@ref)
