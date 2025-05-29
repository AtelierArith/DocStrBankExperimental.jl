```
BreakpointRef(framecode, stmtidx)
BreakpointRef(framecode, stmtidx, err)
```

A reference to a breakpoint at a particular statement index `stmtidx` in `framecode`. If the break was due to an error, supply that as well.

Commands that execute complex control-flow (e.g., `next_line!`) may also return a `BreakpointRef` to indicate that the execution stack switched frames, even when no breakpoint has been set at the corresponding statement.
