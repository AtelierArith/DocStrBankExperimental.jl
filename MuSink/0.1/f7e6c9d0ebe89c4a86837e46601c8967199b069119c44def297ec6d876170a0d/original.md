```
cost(coupling; weighted = true, keep_batchdim = false)
cost(workspace, a, b; weighted = true, keep_batchdim = false)
```

Calculate the total transport cost for a `coupling` along the edge `(a, b)`. If `keep_batchdim = true`, the batch dimension is retained even if the batchsize of `workspace` is one. If `weighted = true`, the cost value is scaled by the edge weight.
