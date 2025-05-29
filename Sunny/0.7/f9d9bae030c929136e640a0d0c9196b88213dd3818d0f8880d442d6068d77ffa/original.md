```
repeat_periodically(sys::System, counts::NTuple{3, Int})
```

Creates a [`System`](@ref) identical to `sys` but repeated a given number of times along each system axis according to the specified `counts`. This is a special case of the more general [`reshape_supercell`](@ref).

See also [`repeat_periodically_as_spiral`](@ref), which rotates the spins between periodic copies.
