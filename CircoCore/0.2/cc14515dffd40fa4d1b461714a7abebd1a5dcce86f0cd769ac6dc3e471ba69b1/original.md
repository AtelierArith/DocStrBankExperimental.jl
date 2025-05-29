```
die(service, me::Actor; exit=false)
```

Permanently unschedule the actor from its current scheduler.

if `exit` is true and this is the last actor on its scheduler, the scheduler will be terminated.
