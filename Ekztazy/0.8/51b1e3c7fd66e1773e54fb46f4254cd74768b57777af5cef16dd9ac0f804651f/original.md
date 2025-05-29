```
@deferred_fetch [functions...] block
```

Identical to [`@fetch`](@ref), but `Future`s are not `fetch`ed until the **end** of the block. This is more efficient, but only works when there are no data dependencies in the block.

## Examples

This will work:

```julia
@deferred_fetch begin
    guild_resp = create(c, Guild; name="foo")
    channel_resp = retrieve(c, DiscordChannel, 123)
end
```

This will not, because the second call is dependent on the first value:

```julia
@deferred_fetch begin
    guild_resp = create(c, Guild; name="foo")
    channels_resp = retrieve(c, DiscordChannel, guild_resp.val)
end
```
