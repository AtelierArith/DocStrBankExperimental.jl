```
addr(a::Actor)
```

Return the address of the actor.

Call this on a spawned actor to get its address. Throws `UndefRefError` if the actor is not spawned.
