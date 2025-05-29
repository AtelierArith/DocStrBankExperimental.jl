```
eigenvaluesInGrid(
    m::AIMSteppingMethod,
    p::NumericAIMProblem{N,T},
    c::AIMCache{N,T},
    grid::Tuple{T,T,Int64,Int64};
    xtol::Real = 1.0e-10,
    ftol::Real = 1.0e-10,
    iterations::Int = 1000
    ) where {N <: Unsigned, T <: Complex}
```

Attempts to find eigenvalues using a grid of complex plane data points as initial guesses passed to nlsolve.

# Input

  * `m::AIMSteppingMethod`: The stepping method to use.
  * `p::NumericAIMProblem{N,T}`: The previously defined problem data.
  * `c::AIMCache{N,T}`: The cache constructed from p.
  * `grid::Tuple{T,T,Int64,Int64}`: A tuple consisting of (start point, end point, num. of real pts., num. of imag. pots.).
  * `xtol::Real`: Norm difference in x between two successive iterates under which convergence is declared.
  * `ftol::Real`: Infinite norm of residuals under which convergence is declared.
  * `iterations::Int`: Maximum number of iterations performed by NLsolve.

# Output

An object of type `Array{T,1}` containing the modes found within the grid.
