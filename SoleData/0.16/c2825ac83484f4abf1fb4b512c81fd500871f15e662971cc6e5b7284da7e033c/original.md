```
struct Feature{A} <: AbstractFeature
    atom::A
end
```

A feature solely identified by an atom (e.g., a string with its name, a tuple of strings, etc.)

See also [`AbstractFeature`](@ref).
