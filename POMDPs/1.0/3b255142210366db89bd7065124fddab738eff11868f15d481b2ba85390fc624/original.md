```
initialize_belief(updater::Updater,
                     state_distribution::Any)
initialize_belief(updater::Updater, belief::Any)
```

Returns a belief that can be updated using `updater` that has similar distribution to `state_distribution` or `belief`.

The conversion may be lossy. This function is also idempotent, i.e. there is a default implementation that passes the belief through when it is already the correct type: `initialize_belief(updater::Updater, belief) = belief`
