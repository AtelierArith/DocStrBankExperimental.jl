```
unitary_free_phase_fidelity(
    U::AbstractMatrix,
    U_goal::AbstractMatrix,
    phases::AbstractVector{<:Real},
    phase_operators::AbstractVector{<:AbstractMatrix};
    subspace::AbstractVector{Int}=axes(U, 1)
)
```

Calculate the fidelity between unitary operators `U` and `U_goal` in the `subspace`, including the `phase` rotations about the `phase_operators`.
