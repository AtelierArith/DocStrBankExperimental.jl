```
`update_and_stop!(stp :: AbstractStopping; kwargs...)`
```

Update the values in the state and return the optimality status of the problem as a boolean.

Note: Kwargs are forwarded to the `update!` call.
