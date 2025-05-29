```
disconnect(lk::Link)
```

Remove the connection between the calling actor and the actor represented by `lk`.

**Note:** If this is called from the `Main` scope, `lk`  is disconnected from the `_ROOT` actor.
