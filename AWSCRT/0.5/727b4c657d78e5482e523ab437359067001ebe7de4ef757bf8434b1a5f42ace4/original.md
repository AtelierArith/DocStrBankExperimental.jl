```
wait_until_synced(sf::ShadowFramework)
```

Blocks until the next time the shadow document is synchronized with the broker.

!!! warning "Warning: Race Condition"
    If you are using this function to publish a message and then wait for the following synchronization, you must use the `do` form of [`wait_until_synced`](@ref) instead which accepts a lambda as the first argument. Otherwise, your publish will race the synchronization and there is a chance the synchronization will finish before you begin waiting for it (so you miss the edge and your program hangs).

