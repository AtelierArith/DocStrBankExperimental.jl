```
box(a::Actor)
```

Return the 'P.O. box' of the spawned actor.

Call this on a spawned actor to get its id (aka box). Throws `UndefRefError` if the actor is not spawned.
