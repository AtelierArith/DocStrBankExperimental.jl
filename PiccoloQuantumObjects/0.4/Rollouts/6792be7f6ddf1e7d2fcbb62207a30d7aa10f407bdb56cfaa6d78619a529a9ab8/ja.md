```
unitary_free_phase_fidelity(
    U::AbstractMatrix,
    U_goal::AbstractMatrix,
    phases::AbstractVector{<:Real},
    phase_operators::AbstractVector{<:AbstractMatrix};
    subspace::AbstractVector{Int}=axes(U, 1)
)
```

ユニタリ演算子 `U` と `U_goal` の間の忠実度を `subspace` で計算し、`phase_operators` に関する `phase` 回転を含みます。
