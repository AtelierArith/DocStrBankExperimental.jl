```julia
write_set(
    exo::Exodus.ExodusDatabase{M, I, B, F},
    set::Exodus.AbstractExodusSet
)

```

型を指定することで、非一致の型を持つセットをエクソダスファイルに書き込まないようにします。
