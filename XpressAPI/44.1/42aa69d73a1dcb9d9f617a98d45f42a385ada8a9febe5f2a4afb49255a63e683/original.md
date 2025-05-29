```
XPRSaddcbnewnode(prob, cb, priority)
```

# Arguments

  * `cbprob`: The problem passed to the callback function, `newnode`.
  * `parentnode`: Unique identifier for the parent of the new node.
  * `node`: Unique identifier assigned to the new node.
  * `branch`: The sequence number of the new node amongst the child nodes of `parentnode`. For regular branches on a MIP entity this will be either `0` or `1`.

`cb` will be invoked with this signature:

```
cb(cbprob, parentnode, node, branch)::Nothing
```
