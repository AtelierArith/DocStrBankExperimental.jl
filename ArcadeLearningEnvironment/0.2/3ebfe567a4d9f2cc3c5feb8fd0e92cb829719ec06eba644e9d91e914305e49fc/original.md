```
cloneSystemState(ale_instance::ALEPtr)
```

This makes a copy of the system & environment state, suitable for serialization. This includes pseudorandomness and so is *not* suitable for planning purposes.
