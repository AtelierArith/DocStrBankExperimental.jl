```
measure(state, args[, t])
measure(state, measure[, t])
measure(state, [measures...][, t])
```

compute the requested measurements on the given state and simulation time

It is more efficient to ask all required measurements in one call

# Examples

```
measure(state, X(1))     # compute observable X(1)
measure(state, X)        # compute observable X on all sites
measure(state, (X, Y))   # compute correlations XY on all pairs of sites
measure(state, Check("check", X(1)X(2), t->sin(2t)), 0.8) # compute and check the given observable against a computed value
measure(state, [X(2), Y, (X, Y)]) # several measures together
```
