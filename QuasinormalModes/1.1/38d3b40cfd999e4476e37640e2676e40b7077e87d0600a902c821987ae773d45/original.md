```
computeEigenvalues(
    m::AIMSteppingMethod,
    p::QuadraticEigenvalueProblem{N,T},
    c::AIMCache{N,Polynomial{T}};
    plr_polish::Bool = true, 
    plr_epsilon::Real = convert(T, 1.0e-10)
    ) where {N <: Unsigned, T <: Number}
```

Compute the eigenvalues for the problem `p` with corresponding cache `c`.

# Input

  * `m::AIMSteppingMethod`: The stepping method to use.
  * `p::QuadraticEigenvalueProblem`: The previously defined problem data.
  * `c::AIMCache`: The cache constructed from p.
  * `plr_polish::Bool`: Tell PolynomialRoots to divide the original polynomial by each root found and polish the results using the full polynomial.
  * `plr_epsilon::Real`: The stopping criterion described in Skowron & Gould paper. This is not the precision with which the roots will be calculated.

# Output

An object of type `Array{T,1}` containing the computed eigenvalues.
