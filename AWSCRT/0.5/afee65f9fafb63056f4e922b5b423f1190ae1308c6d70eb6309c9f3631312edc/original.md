```
unsubscribe(sf::ShadowFramework)
```

Unsubscribes from the shadow document's topics and stops processing updates. After calling this, `wait_until_synced(sf)` will again block until the first publish in response to calling `subscribe(sf)`.

Returns a task which completes when the tasks from each [`unsubscribe`](@ref) call complete. Also returns a collection containing the packet ID from each [`unsubscribe`](@ref) call.
