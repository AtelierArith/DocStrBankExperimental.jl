```
objective(workspace; keep_batchdim = false)
```

The dual unbalanced multi-marginal optimal transport objective. If `keep_batchdim = true`, the batch dimension is retained even if the batchsize of `workspace` is one.

In theory, this value should monotonically increase with the number of Sinkhorn steps.

!!! warn
    This function is currently not working as intended.

