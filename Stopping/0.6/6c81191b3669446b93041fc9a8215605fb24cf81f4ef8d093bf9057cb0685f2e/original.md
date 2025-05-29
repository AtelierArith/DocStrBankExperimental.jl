```
`stop!(:: AbstractStopping; kwargs...)`
```

Update the Stopping and return a boolean true if we must stop.

It serves the same purpose as `start!` in an algorithm; telling us if we stop the algorithm (because we have reached optimality or we loop infinitely, etc).

The function `stop!` successively calls: `_domain_check`, `_optimality_check`, `_null_test`, `_unbounded_check!`, `_tired_check!`, `_resources_check!`, `_stalled_check!`, `_iteration_check!`, `_main_pb_check!`, `add_to_list!`

Note:

  * kwargs are sent to the `_optimality_check!` call.
  * If `listofstates != VoidListofStates`, call `add_to_list!`.
