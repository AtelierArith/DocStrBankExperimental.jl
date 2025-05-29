```
computeEigenvalues(
    m::AIMSteppingMethod,
    p::NumericAIMProblem{N,T},
    c::AIMCache{N,T},
    guess::T;
    nls_xtol::Real = convert(T, 1.0e-10),
    nls_ftol::Real = convert(T, 1.0e-10),
    nls_iterations::Int = 1000
    ) where {N <: Unsigned, T <: Complex}
```

Compute a single eigenvalue for the problem `p` with corresponding cache `c`.

# Input

  * `m::AIMSteppingMethod`: The stepping method to use.
  * `p::NumericAIMProblem`: The previously defined problem data.
  * `c::AIMCache`: The cache constructed from p.
  * `nls_xtol::Real`: Norm difference in x between two successive iterates under which convergence is declared.
  * `nls_ftol::Real`: Infinite norm of residuals under which convergence is declared.
  * `nls_iterations::Int`: Maximum number of iterations performed by NLsolve.

# Output

An object of type `SolverResults` returned by `nlsolve`. See [NLsolve.jl](https://github.com/JuliaNLSolvers/NLsolve.jl) for further details.
