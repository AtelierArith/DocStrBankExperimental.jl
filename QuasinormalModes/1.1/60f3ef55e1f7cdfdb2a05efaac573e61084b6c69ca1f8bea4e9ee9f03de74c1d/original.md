```
computeEigenvalues(
    m::AIMSteppingMethod,
    p::NumericAIMProblem{N,T},
    c::AIMCache{N,T},
    guess::T;
    roots_atol::Real = 1.0e-10,
    roots_rtol::Real = 1.0e-10,
    roots_xatol::Real = 1.0e-10,
    roots_xrtol::Real = 1.0e-10,
    roots_maxevals::Int = 100
    ) where {N <: Unsigned, T <: Real}
```

Compute a single eigenvalue for the problem `p` with corresponding cache `c`. For details on convergence settings see [Roots.jl](https://juliahub.com/docs/Roots/o0Xsi/1.0.7/reference/#Convergence).

# Input

  * `m::AIMSteppingMethod`: The stepping method to use.
  * `p::NumericAIMProblem{N,T}`: The previously defined problem data.
  * `c::AIMCache{N,T}`: The cache constructed from p.
  * `grid::Tuple{T,T}`: A tuple consisting of (start point, end point).
  * `roots_atol::Real`: Absolute tolerance.
  * `roots_rtol::Real`: Relative tolerance.
  * `roots_xatol::Real`: Floating point comparison absolute tolerance.
  * `roots_xrtol::Real`: Floating point comparison relative tolerance.
  * `roots_maxevals::Int`: Number of algorithm iterations performed.

# Output

An object of type T containing the found eigenvalue.
