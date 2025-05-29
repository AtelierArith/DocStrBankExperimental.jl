```
log_weights = get_log_weights(state::ParticleFilterState)
```

Return the vector of log weights for the current state, one for each particle.

The weights are not normalized, and are in log-space.
