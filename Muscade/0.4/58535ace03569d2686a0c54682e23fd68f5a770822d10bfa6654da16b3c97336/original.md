```
scale = studyscale(state;[verbose=false],[dbg=(;)])
```

Returns a named tuple of named tuples for scaling the model, accessed as     `scaled.myclass.myfield`, for example `scale.X.tx1`.

!!! info
    Currently, the format of `scale` is not identical to the input expected by `setscale!`: work in progress


If `verbose=true`, prints out a report of the analysis underlying the proposed `scale`.  The proposed scaling depends on the `state` passed as input - as it is computed for a given incremental matrix.

See also: [`setscale!`](@ref)
