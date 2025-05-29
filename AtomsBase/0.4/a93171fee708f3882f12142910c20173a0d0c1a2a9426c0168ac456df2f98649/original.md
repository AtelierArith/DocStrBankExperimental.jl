```
atomic_number(sys::AbstractSystem, i)
atomic_number(species)
```

Vector of atomic numbers in the system `sys` or the atomic number of a particular `species` / the `i`th species in `sys`.

The intention is that [`atomic_number`](@ref) carries the meaning of identifying the type of a `species` (e.g. the element for the case of an atom), whereas [`atomic_symbol`](@ref) may return a more unique identifier. For example for a deuterium atom this may be `:D` while `atomic_number` is still `1`.
