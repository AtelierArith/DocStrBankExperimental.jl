```
`update_and_start!(stp::AbstractStopping; no_opt_check::Bool = false, kwargs...)`
```

Update values in the State and initialize the Stopping. Returns the optimality status of the problem as a boolean.

Note: 

  * Kwargs are forwarded to the `update!` call.
  * `no_opt_check` skip optimality check in `start!` (`false` by default).
