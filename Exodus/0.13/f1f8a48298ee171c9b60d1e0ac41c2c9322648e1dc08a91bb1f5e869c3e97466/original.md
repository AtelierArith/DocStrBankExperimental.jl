```julia
write_values(
    exo::Exodus.ExodusDatabase,
    t::Type{Exodus.GlobalVariable},
    timestep::Integer,
    var_values::Vector{<:AbstractFloat}
)

```

Wrapper method for global variables around the main write*values method write*values(   exo::ExodusDatabase, t::Type{GlobalVariable},    timestep::Integer, var*values::Vector{<:AbstractFloat} ) = write*values(exo, t, timestep, 1, 1, var_values)

Note: you need to first run write*number*of_variables(exo, GlobalVariable, n) where n is the number of variables.

Example: write*number*of*variables(exo, GlobalVariable, 5) write*values(exo, GlobalVariable, 1, [10.0, 20.0, 30.0, 40.0, 50.0])
