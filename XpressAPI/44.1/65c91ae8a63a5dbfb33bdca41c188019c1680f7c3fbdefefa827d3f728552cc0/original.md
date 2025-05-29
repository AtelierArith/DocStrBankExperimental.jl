```
XPRSaddcbchgbranchobject(prob, cb, priority)
```

# Arguments

  * `cbprob`: The problem passed to the callback function, `chgbranchobject`.
  * `branch`: The candidate branching data selected by the Optimizer. Will be `nothing` if no candidates exist.
  * `newbranch`: Optional new branching data to replace the Optimizer's selection. If `branch` or `nothing` is passed back, no change will be applied.

`cb` will be invoked with this signature:

```
cb(cbprob, branch)::newbranch
```
