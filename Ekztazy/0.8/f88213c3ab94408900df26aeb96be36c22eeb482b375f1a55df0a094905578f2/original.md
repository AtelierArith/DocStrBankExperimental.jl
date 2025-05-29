```
update(c::Client, x::T, args...; kwargs...) -> Future{Response}
```

Update, edit, modify, etc.

## Examples

Editing a [`Message`](@ref):

```julia
update(c, message; content="foo2")
```

Modifying a [`Webhook`](@ref):

```julia
update(c, webhook; name="bar2")
```

Updating a [`Role`](@ref):

```julia
update(c, role, guild; permissions=8)
```
