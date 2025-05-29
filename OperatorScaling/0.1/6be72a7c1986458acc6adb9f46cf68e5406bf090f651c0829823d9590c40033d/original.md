```
A_scaled, D1, D2 = equilibrate(A::AbstractMatrix{T}; A_transposed = false, kwargs...)
```

Performs the equilibration algorithm on the matrix `A` and returns the scaled matrix matrix `A_scaled` with its diagonal scaling factors `D1` and `D2`.

```
Q_scaled, D = equilibrate(Q::Symmetric{T}; kwargs...) where {T}
```

Performs the equilibration algorithm on the symmetric matrix `Q` and returns the scaled matrix matrix `Q_scaled` with its diagonal scaling factor `D`.

See [`equilibrate!`](@ref) for the keyword arguments.
