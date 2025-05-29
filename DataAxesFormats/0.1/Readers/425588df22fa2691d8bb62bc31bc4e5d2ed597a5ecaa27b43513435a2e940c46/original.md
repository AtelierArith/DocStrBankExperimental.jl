```
scalars_set(daf::DafReader)::AbstractSet{<:AbstractString}
```

The names of the scalar properties in `daf`.

!!! note
    There's no immutable set type in Julia for us to return. If you do modify the result set, bad things *will* happen.

