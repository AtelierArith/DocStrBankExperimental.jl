```
StorageScalarBase = Union{StorageReal, AbstractString}
```

For using in `where` clauses when a type needs to be a [`StorageScalar`](@ref). That is, write `where {T <: StorageScalarBase}` instead of `where {T <: StorageScalar}`, because of the limitations of Julia's type system.
