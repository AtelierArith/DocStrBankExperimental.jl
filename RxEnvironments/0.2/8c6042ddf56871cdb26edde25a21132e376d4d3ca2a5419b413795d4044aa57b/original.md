```
update!(e::AbstractEntity{T,ContinuousEntity,E}) where {T,E}
```

Update the state of the entity `e` based on its current state and the time elapsed since the last update. Acts as state transition function.

# Arguments

  * `e::AbstractEntity{T,ContinuousEntity,E}`: The entity to update.
