```
nearest_cor!(A, alg=nothing; kwargs...)
```

Return the nearest positive definite correlation matrix to $A$. This method will overwrite $A$.

This is a "batteries included" method, and is designed to just work with as little thought as possible. Unlike `solve!`, this method will return the nearest correlation matrix directly instead of a `NCMSolution` object. Additionally the solution is checked to be positive definite, and corrected if it is not.

# Examples

```julia-repl
julia> import LinearAlgebra: isposdef

julia> r = [
    1.00 0.82 0.56 0.44
    0.82 1.00 0.28 0.85
    0.56 0.28 1.00 0.22
    0.44 0.85 0.22 1.00
];

julia> isposdef(r)
false

julia> nearest_cor!(r)
4×4 Matrix{Float64}:
 1.0       0.817095  0.559306  0.440514
 0.817095  1.0       0.280196  0.847352
 0.559306  0.280196  1.0       0.219582
 0.440514  0.847352  0.219582  1.0

julia> isposdef(r)
true
```
