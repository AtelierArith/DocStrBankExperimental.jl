```
vectors_set(daf::DafReader, axis::AbstractString)::AbstractSet{<:AbstractString}
```

The names of the vector properties for the `axis` in `daf`, **not** including the special `name` property.

This first verifies the `axis` exists in `daf`.

!!! note
    There's no immutable set type in Julia for us to return. If you do modify the result set, bad things *will* happen.

