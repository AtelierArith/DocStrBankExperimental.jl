```
State( ρ :: Matrix{T<:Number} ) <: Operator{T}
```

The density matrix representation of a quantum state. The constructor, `State(ρ)` throws a `DomainError` if [`is_density_matrix`](@ref) evaluates to `false`.
