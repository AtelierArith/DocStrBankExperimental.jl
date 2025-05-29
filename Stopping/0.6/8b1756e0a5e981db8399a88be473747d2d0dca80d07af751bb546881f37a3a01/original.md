```
`start!(stp::AbstractStopping; no_opt_check::Bool = false, kwargs...)`
```

Update the Stopping and return `true` if we must stop.

Purpose is to know if there is a need to even perform an optimization algorithm or if we are at an optimal solution from the beginning.  Set `no_opt_check` to `true` avoid checking optimality and domain errors.

The function `start!` successively calls: `_domain_check(stp, x)`, `_optimality_check!(stp, x)`, `_null_test(stp, x)` and  `_user_check!(stp, x, true)`.

Note: - `start!` initializes `stp.meta.start_time` (if not done before), `stp.current_state.current_time` and `stp.meta.optimality0`  (if `no_opt_check` is false).           - Keywords argument are passed to the `_optimality_check!` call.           - Compatible with the `StopRemoteControl`.   
