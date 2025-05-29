```
@fetch [functions...] block
```

Wrap all calls to the specified CRUD functions ([`create`](@ref), [`retrieve`](@ref), [`update`](@ref), and [`delete`](@ref)) with `fetch` inside a block. If no functions are specified, all CRUD functions are wrapped.

## Examples

Wrapping all CRUD functions:

```julia
@fetch begin
    guild_resp = create(c, Guild; name="foo")
    guild_resp.ok || error("Request for new guild failed")
    channel_resp = retrieve(c, DiscordChannel, guild_resp.val)
end
```

Wrapping only calls to `retrieve`:

```julia
@fetch retrieve begin
    resp = retrieve(c, DiscordChannel, 123)
    future = create(c, Message, resp.val; content="foo")  # Behaves normally.
end
```
