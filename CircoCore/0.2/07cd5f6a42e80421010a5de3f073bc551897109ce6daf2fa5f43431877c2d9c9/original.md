```
Addr(postcode::PostCode, box::ActorId)
Addr(readable_address::String)
Addr()
```

The full address of an actor.

When created without arguments, it will be the null address. See [`isnulladdr()`](@ref)

If the referenced actor migrates to a different scheduler, messages sent to the old address will bounce back as [`RecipientMoved`](@ref) and the Addr must be updated manually.

# Examples

Addr("192.168.1.11:24721", 0xbc6ac81fc7e4ea2)

Addr("192.168.1.11:24721/bc6ac81fc7e4ea2")
