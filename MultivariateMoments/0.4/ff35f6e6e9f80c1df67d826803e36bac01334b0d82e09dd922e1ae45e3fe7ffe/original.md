```
struct MomentMatrixWeightSolver
    rtol::T
    atol::T
end
```

Given a moment matrix `ν` and the atom centers, determine the weights by solving a linear system over all the moments of the moment matrix, keeping duplicates (e.g., entries corresponding to the same monomial).

If the moment values corresponding to the same monomials are known to be equal prefer [`MomentVectorWeightSolver`](@ref) instead.
