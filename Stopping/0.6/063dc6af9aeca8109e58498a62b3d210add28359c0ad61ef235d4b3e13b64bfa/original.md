```
`cheap_stop!(:: AbstractStopping; kwargs...)`
```

Update the Stopping and return a boolean true if we must stop.

It serves the same purpose as `stop!`, but avoids any potentially expensive checks. We no longer browse `x` and `res` in the State, and no check on the `main_stp`. Check only the updated entries in the meta.

The function `cheap_stop!` successively calls: `_null_test`, `_unbounded_check!`, `_tired_check!`, `_resources_check!`, `_stalled_check!`, `_iteration_check!`, `add_to_list!`

Note:

  * kwargs are sent to the `_optimality_check!` call.
  * If `listofstates != VoidListofStates`, call `add_to_list!`.
