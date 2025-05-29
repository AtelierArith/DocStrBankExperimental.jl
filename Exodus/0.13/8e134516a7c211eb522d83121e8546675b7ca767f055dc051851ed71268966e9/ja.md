```julia
read_values(
    exo::Exodus.ExodusDatabase,
    t::Type{Exodus.NodalVariable},
    timestep::Integer,
    index::Integer
) -> Any

```

ノード変数のラッパーメソッド
