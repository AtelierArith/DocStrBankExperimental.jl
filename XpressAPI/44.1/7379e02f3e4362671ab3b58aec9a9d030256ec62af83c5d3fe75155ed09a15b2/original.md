```
XPRSaddcbnodecutoff(prob, cb, priority)
```

# Arguments

  * `cbprob`: The problem passed to the callback function, `nodecutoff`.
  * `node`: The node id of the node that is cut off. This id cannot be queried from the CURRENTNODE attribute as for other callbacks since this callback is not invoked in the context of the node being cutoff.

`cb` will be invoked with this signature:

```
cb(cbprob, node)::Nothing
```
