```
delete(c::Client, x::T, args...) -> Future{Response}
```

Delete, remove, discard, etc.

## Examples

Kicking a [`Member`](@ref):

```julia
delete(c, member)
```

Unbanning a [`Member`](@ref):

```julia
delete(c, ban, guild)
```

Deleting all [`Reaction`](@ref)s from a [`Message`](@ref) (note: this is the only update/delete method which takes a type parameter):

```julia
delete(c, Reaction, message)
```
