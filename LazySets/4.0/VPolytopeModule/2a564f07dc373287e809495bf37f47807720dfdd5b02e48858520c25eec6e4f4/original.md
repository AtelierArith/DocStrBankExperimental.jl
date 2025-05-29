```
constraints_list(P::VPolytope)
```

### Algorithm

For one- and two-dimensional sets, we respectively convert to an `Interval` or a `VPolytope` and call the corresponding `constraints_list` function. For higher-dimensional sets, we use `tohrep` to compute the constraint representation and call the corresponding `constraints_list` function.
