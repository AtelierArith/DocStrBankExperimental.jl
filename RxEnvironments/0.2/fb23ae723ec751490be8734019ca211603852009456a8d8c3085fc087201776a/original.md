```
terminate!(entity::AbstractEntity)
```

Terminate an entity by setting its `is_terminated` flag to `true` and severing off all subscriptions to and from the entity.

# Arguments

  * `entity::AbstractEntity`: The entity to terminate.
