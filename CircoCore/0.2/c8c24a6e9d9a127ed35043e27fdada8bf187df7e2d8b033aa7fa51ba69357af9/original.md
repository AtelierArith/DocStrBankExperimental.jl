```
OnBecome(reincarnation::Actor)
```

Actor lifecycle message marking the `become()` action.

`reincarnation` points to the new incarnation of the actor. `me` is scheduled at the delivery time of this message, `reincarnation` is not.

Exceptions thrown while handling `OnBecome``will propagate to the initiating`become` call.
