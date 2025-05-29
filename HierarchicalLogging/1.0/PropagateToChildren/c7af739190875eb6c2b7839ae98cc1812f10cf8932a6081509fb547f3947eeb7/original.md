```
PropagateToChildren.Mode
```

When a message is received by a `logger`, determines how it will be propagted to its children

  * `PropagateToChildren.AllChildren`: Propagate message to all children of `logger`
  * `PropagateToChildren.DirectChildren`: Propagate message to direct children only (e.g., if a message is received by logger "A.B", it will be forwarded to "A.B.C" (if present) but not "A.B.C.D")
  * `PropagateToChildren.None`: Do not propagate message to child loggers
