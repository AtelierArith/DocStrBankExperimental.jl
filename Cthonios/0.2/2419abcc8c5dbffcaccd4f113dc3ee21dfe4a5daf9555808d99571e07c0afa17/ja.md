```julia
create_fields(
    domain::Cthonios.Domain
) -> Union{FiniteElementContainers.SimpleNodalField{_A, 2, _B, _C, A} where {_A<:Number, _B, _C, A<:AbstractMatrix{_A}}, FiniteElementContainers.VectorizedNodalField{_A, 2, _B, _C, A} where {_A<:Number, _B, _C, A<:AbstractVector{_A}}}

```

`domain.dof`に基づいてゼロフィールドを作成します。
