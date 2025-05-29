```
freeze(record)
```

Freezes an allocation `record`, to not allow new allocations to be added. This converts the memory of the what happenned to be stored as a `Tuple`. This could give better performance during replay; or it could give worse.
