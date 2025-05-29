```
target(ws::Workspace, node; keep_batchdim = false)
```

The target measure at `node` with respect to the counting measure.

If `keep_batchdim = true`, the singular batch dimension in case of batchsize 1 is not dropped.
