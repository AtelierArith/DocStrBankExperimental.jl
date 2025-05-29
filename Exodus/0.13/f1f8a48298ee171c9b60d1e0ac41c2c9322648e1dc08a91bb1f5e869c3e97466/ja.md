```julia
write_values(
    exo::Exodus.ExodusDatabase,
    t::Type{Exodus.GlobalVariable},
    timestep::Integer,
    var_values::Vector{<:AbstractFloat}
)

```

グローバル変数のラッパーメソッドは、メインの write*values メソッドの周りにあります write*values(   exo::ExodusDatabase, t::Type{GlobalVariable},    timestep::Integer, var*values::Vector{<:AbstractFloat} ) = write*values(exo, t, timestep, 1, 1, var_values)

注: まず write*number*of_variables(exo, GlobalVariable, n) を実行する必要があります。ここで n は変数の数です。

例: write*number*of*variables(exo, GlobalVariable, 5) write*values(exo, GlobalVariable, 1, [10.0, 20.0, 30.0, 40.0, 50.0])
