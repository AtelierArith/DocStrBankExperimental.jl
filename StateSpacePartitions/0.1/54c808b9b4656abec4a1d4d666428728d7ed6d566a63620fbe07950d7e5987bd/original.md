```
inverse_iteration(A, x₀, μ₀; tol = 1e-4, maxiter_eig = 10, maxiter_solve = 2, τ = 0.1)
```

# Description

Computes the eigenpair (λ, x) of the matrix A corresponding to initial eigenguess (μ₀, x₀) using inverse iteration.

# Arguments

  * `A::Matrix` - The matrix to compute the eigenpair of.
  * `x₀::Vector` - The initial guess for the eigenvector.
  * `μ₀::Real` - The initial guess for the eigenvalue.

# Keyword Arguments

  * `tol::Real` - The Cauchy-criteria tolerance for the iterative eigensolver.
  * `maxiter_eig::Int` - The maximum number of iterations for the iterative eigensolver.
  * `maxiter_solve::Int` - The maximum number of iterations for the iterative linear solver.
  * `τ::Real` - The drop tolerance for the incomplete LU factorization.

# Returns

  * `x::Vector` - The eigenvector.
  * `λ::Real` - The eigenvalue.
