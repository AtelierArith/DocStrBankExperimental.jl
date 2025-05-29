```julia
read_values(
    exo::Exodus.ExodusDatabase,
    t::Type{Exodus.GlobalVariable},
    timestep::Integer
) -> Vector

```

グローバル変数のラッパーメソッドは、メインの read*values メソッドの周りにあります。 read*values(exo::ExodusDatabase, t::Type{GlobalVariable}, timestep::Integer) = read_values(exo, t, timestep, 1, 1)

例: read_values(exo, GlobalVariable, 1)
