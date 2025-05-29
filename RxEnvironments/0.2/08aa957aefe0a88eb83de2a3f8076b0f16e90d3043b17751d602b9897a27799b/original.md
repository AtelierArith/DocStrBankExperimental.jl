```
add!(first::AbstractEntity{T,S,E}, second; environment=false) where {T,S,E}
```

Adds `second` to `first`. If `environment` is `true`, the `AbstractEntity` created for `second` will be labeled as an environment.  The Markov Blankets for both entities will be subscribed to each other.

# Arguments

  * `first::AbstractEntity{T,S,E}`: The entity to which `second` will be added.
  * `second`: The entity to be added to `first`.
  * `is_active=false`: A boolean indicating whether `second` should be instantiated as an active entity.
