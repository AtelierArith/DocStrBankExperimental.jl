```
Legolas.SchemaVersion(name::AbstractString, version::Integer)
```

Return `Legolas.SchemaVersion{Symbol(name),version}()`.

Throws an `ArgumentError` if `name` is not a valid schema name.

Prefer using this constructor over `Legolas.SchemaVersion{Symbol(name),version}()` directly.
