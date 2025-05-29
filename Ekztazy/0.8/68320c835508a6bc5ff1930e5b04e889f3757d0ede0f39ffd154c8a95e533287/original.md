```
retrieve(c::Client, ::Type{T}, args...; kwargs...) -> Future{Response{T}}
```

Retrieve, get, list, etc.

## Examples

Getting the [`Client`](@ref)'s [`User`](@ref):

```julia
retrieve(c, User)
```

Getting a [`Guild`](@ref)'s [`DiscordChannel`](@ref)s:

```julia
retrieve(c, DiscordChannel, guild)
```

Getting an [`Invite`](@ref) to a [`Guild`](@ref) by code:

```julia
retrieve(c, Invite, "abcdef")
```
