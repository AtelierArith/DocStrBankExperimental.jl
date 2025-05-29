```
struct MomentVectorWeightSolver{T}
    rtol::T
    atol::T
end
```

Given a moment matrix `ν` and the atom centers, first convert the moment matrix to a vector of moments, using [`measure(ν; rtol=rtol, atol=atol)`](@ref measure) and then determine the weights by solving a linear system over the monomials obtained.

If the moment values corresponding to the same monomials can have small differences, [`measure`](@ref) can throw an error if `rtol` and `atol` are not small enough. Alternatively to tuning these tolerances [`MomentVectorWeightSolver`](@ref) can be used instead.
