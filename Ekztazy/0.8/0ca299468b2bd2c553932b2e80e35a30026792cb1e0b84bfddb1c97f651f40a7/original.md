```
create(c::Client, ::Type{T}, args...; kwargs...) -> Future{Response}
```

Create, add, send, etc.

## Examples

Sending a [`Message`](@ref):

```julia
create(c, Message, channel; content="foo")
```

Creating a new [`DiscordChannel`](@ref):

```julia
create(c, DiscordChannel, guild; name="bar")
```

Banning a [`Member`](@ref):

```julia
create(c, Ban, guild, member; reason="baz")
```
