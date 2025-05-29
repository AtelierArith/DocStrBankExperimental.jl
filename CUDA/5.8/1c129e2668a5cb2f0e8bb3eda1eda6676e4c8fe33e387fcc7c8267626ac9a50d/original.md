```
update(exec::CuGraphExec, graph::CuGraph; [throw_error::Bool=true])
```

Check whether an executable graph can be updated with a graph and perform the update if possible. Returns a boolean indicating whether the update was successful. Unless `throw_error` is set to false, also throws an error if the update failed.
