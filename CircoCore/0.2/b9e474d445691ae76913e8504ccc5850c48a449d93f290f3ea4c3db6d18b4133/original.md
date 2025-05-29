```
become(service, old::Actor, reincarnated::Actor)
```

Reincarnates the `old` actor into `new`, meaning that `old` will be unscheduled, and `reincarnated` will be scheduled reusing the address of `old`.

The `onbecome` lifecycle callback will be called.

Note: As the name suggests, `become` is the Circonian way of behavior change.
