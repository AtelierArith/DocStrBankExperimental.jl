```julia
read_values(
    exo::Exodus.ExodusDatabase{M, I, B, F},
    _::Type{V<:Exodus.GlobalVariable},
    timestep::Integer,
    id::Integer,
    var_index::Integer
) -> Vector

```

グローバル変数を読み取るためのメソッド
