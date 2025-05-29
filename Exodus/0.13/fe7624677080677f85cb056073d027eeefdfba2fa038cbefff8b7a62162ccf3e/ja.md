```julia
write_values(
    exo::Exodus.ExodusDatabase,
    t::Type{Exodus.NodalVariable},
    timestep::Integer,
    var_index::Integer,
    var_values::Vector{<:AbstractFloat}
)

```

インデックス番号によるノード変数の書き込み用ラッパー
