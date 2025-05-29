```
box(a::Addr)::ActorId
```

Return the box of the address, that is the id of the actor.

When the actor migrates, its box remains the same, only the PostCode of the address changes.
