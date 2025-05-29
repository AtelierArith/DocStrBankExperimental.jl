```julia
columns(ft)

```

Return the columns in a `NamedTuple`.

Each column is an iterable, but not necessarily an `<: AbstractVector`.

!!! note
    **Never mutate columns obtained by this method**, as that will violate invariants assumed by the implementation. Use `map(collect, columns(ft))` or similar to obtain mutable vectors.

