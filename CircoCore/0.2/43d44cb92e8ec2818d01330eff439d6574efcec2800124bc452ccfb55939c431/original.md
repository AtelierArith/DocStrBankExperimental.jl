```
pos(a::Actor)::Pos
```

return the current position of the actor.

Call this on a spawned actor to get its position. Throws `UndefRefError` if the actor is not spawned.
