```julia
read_values(
    exo::Exodus.ExodusDatabase,
    t::Type{Exodus.GlobalVariable},
    timestep::Integer
) -> Vector

```

Wrapper method for global variables around the main read*values method read*values(exo::ExodusDatabase, t::Type{GlobalVariable}, timestep::Integer) = read_values(exo, t, timestep, 1, 1)

Example: read_values(exo, GlobalVariable, 1)
