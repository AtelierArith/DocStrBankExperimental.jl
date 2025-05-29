```
solver_name(model::Model)
```

If available, returns the `SolverName` property of the underlying optimizer.

Returns `"No optimizer attached"` in `AUTOMATIC` or `MANUAL` modes when no optimizer is attached.

Returns `"SolverName() attribute not implemented by the optimizer."` if the attribute is not implemented.
