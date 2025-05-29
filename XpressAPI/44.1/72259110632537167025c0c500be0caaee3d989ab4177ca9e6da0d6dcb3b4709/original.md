```
XPRSaddcbpreintsol(prob, cb, priority)
```

# Arguments

  * `cbprob`: The problem passed to the callback function, `preintsol`.
  * `soltype`: The type of MIP solution that has been found: 0The continuous relaxation solution to the current node of the tree search, which has been found to be integer feasible. 1A MIP solution found by a heuristic. 2A MIP solution provided by the user.
  * `reject`: Set this to 1 if the solution should be rejected. When `soltype` is zero, this will also drop the node problem.
  * `cutoff`: The new cutoff value that the Optimizer will use if the solution is accepted. If the user changes `p_cutoff`, the new value will be used instead. The cutoff value will not be updated if the solution is rejected.

`cb` will be invoked with this signature:

```
cb(cbprob, soltype, cutoff)::reject, cutoff
```
