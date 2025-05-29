```
XPRSaddcboptnode(prob, cb, priority)
```

# Arguments

  * `cbprob`: The problem passed to the callback function, `optnode`.
  * `infeasible`: The feasibility status. If set to a nonzero value by the user, the current node will be declared infeasible.

`cb` will be invoked with this signature:

```
cb(cbprob)::infeasible
```
