```
tspan(fp::AbstractFlowpipe)
```

Return time span of this flowpipe.

### Input

  * `fp` – flowpipe

### Output

The interval representing the time span of the given flowpipe. The fallback is computed as `(tstart(fp), tend(fp))`, see `tstart(::AbstractFlowpipe)` and `tend(::AbstractFlowpipe)` for details.
