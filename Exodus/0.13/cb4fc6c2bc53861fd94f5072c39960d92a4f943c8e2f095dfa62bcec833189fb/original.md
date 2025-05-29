```julia
write_set(
    exo::Exodus.ExodusDatabase{M, I, B, F},
    set::Exodus.AbstractExodusSet
)

```

Typing ensures we don't write a set with non-matching types to the exodus file.
