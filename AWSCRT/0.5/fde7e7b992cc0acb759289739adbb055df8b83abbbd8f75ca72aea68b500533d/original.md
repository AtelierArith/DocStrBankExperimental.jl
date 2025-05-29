```
wait_until_synced(f::Function, sf::ShadowFramework)
```

Blocks until the next time the shadow document is synchronized with the broker. If you want to wait for a synchronization after a publication that you make, then you must make that publication inside the lambda `f`.
