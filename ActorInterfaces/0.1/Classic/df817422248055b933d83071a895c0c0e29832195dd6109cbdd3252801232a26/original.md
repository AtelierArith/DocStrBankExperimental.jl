```
become(behavior, [ctx])
```

Replace the behavior of the current actor with `behavior`. 

The new behavior will be effective at the processing of the next message.

The ctx argument can be automatically injected by [`@ctx`](@ref).
