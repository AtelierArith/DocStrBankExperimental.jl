```julia
kron(A, B)

```

Construct a lazy representation of the Kronecker product `A ⊗ B`. One of the two factors can be an `AbstractMatrix`, which is then promoted to a `MatrixOperator` automatically. To avoid fallback to the generic [`Base.kron`](@ref), at least one of `A` and `B` must be an `AbstractSciMLOperator`.
