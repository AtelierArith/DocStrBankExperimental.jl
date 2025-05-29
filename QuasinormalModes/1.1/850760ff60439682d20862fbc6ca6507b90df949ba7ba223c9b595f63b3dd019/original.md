```
AIMCache(p::QuadraticEigenvalueProblem{N,T}) where {N <: Unsigned, T <: Number}
```

Create an AIMCache object suitable for Quadratic Eigenvalue Problems.

# Input

  * `p::QuadraticEigenvalueProblem`: The problem data.

# Output

An `AIMCache{N,Polynomial{T}}` object.
