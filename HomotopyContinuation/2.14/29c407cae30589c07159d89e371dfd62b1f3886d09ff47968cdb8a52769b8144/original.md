```
solution_approximation(certificate::AbstractSolutionCertificate)
```

If `is_certified(certificate)` is `true` this returns the midpoint of the [`certified_solution_interval`](@ref) of the given `certificate` as a `Vector{ComplexF64}`. Returns `nothing` if `is_certified(certificate)` is `false`.
