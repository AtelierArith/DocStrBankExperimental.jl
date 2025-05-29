```julia
remove_atom!(frame::Chemfiles.Frame, index::Integer)

```

Remove the `atom` at `index` from the `frame`.

This function modifies all the `atoms` indexes after `index`, and invalidates any array obtained using `positions` or `velocities`.
