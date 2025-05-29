```
OnSpawn
```

Actor lifecycle message that marks the first scheduling of the actor, sent during spawning, before any other message.

# Examples

```julia
CircoCore.onmessage(me::MyActor, ::OnSpawn, service) = begin
    registername(service, "MyActor", me) # Register this actor in the local name service
end
```
