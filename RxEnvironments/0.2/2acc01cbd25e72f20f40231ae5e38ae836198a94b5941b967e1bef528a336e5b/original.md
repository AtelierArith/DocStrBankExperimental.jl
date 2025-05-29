```
create_entity(entity; is_discrete = false, is_active = false, real_time_factor = 1)
```

Creates an `RxEntity` that decorates a given entity. The `is_discrete` and `is_active` parameters determine whether or not the entity lives in a discrete or continuous state-space, and whether or not the entity is active or passive. The `real_time_factor` parameter determines how fast the entity's clock ticks. This function can be used as a lower-level API in order to create a more complex network of entities.
