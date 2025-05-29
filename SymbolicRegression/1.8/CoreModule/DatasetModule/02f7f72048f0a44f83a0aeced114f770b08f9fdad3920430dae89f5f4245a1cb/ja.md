```
Dataset(X::AbstractMatrix{T},
        y::Union{AbstractVector{T},Nothing}=nothing,
        loss_type::Type=Nothing;
        weights::Union{AbstractVector, Nothing}=nothing,
        variable_names::Union{Array{String, 1}, Nothing}=nothing,
        y_variable_name::Union{String,Nothing}=nothing,
        extra::NamedTuple=NamedTuple(),
        X_units::Union{AbstractVector, Nothing}=nothing,
        y_units=nothing,
) where {T<:DATA_TYPE}
```

内部関数間で渡すためのデータセットを構築します。BasicDatasetを返します。
