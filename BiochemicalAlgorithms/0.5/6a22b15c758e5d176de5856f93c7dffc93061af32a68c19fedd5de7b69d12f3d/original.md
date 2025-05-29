```
atom_by_name(
    ac::AbstractAtomContainer{T} = default_system(),
    name::AbstractString
) -> Union{Nothing, Atom{T}}
```

Returns the first `Atom{T}` associated with the given `name` in `ac`. Returns nothing if no such atom exists.

# Supported keyword arguments

  * `frame_id::MaybeInt = 1`: Any value other than `nothing` limits the result to atoms matching this frame ID.
