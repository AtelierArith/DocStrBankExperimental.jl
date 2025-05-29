```
ParallelProcessingTools.original_exception(err)
```

Replaces (possibly nested) exceptions like a `TaskFailedException` or `RemoteException`s with the innermost exception, likely to be the one that was thrown originally. Leaves other exceptions unchanged.
