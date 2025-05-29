```
XPRSaddcbchgnode(prob, cb, priority)
```

# Arguments

  * `cbprob`: The problem passed to the callback function, `chgnode`.
  * `node`: A pointer to the number of the node selected by the Optimizer. This value cannot be changed.

`cb` will be invoked with this signature:

```
cb(cbprob)::node
```
