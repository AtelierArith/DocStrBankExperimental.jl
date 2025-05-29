```
isunitary(U::QuantumObject; kwargs...)
```

Test whether the [`QuantumObject`](@ref) $U$ is unitary operator. This function calls `Base.isapprox` to test whether $U U^\dagger$ is approximately equal to identity operator.

Note that all the keyword arguments will be passed to `Base.isapprox`.
