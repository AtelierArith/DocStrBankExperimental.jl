```
fit_KPFM!(grid::SpmGrid, response_channel::String;
    sweep_channel::String="", bwd::Bool=true)::Nothing
```

Fits KPFM data. This is done by fitting a parabola to the graoh of `response_channel` vs `sweep_channel` on the grid. If not explicitely specified, `sweep_channel` defaults to the sweep signal of the grid.

For KPFM, the response channel should be the "Frequency Shift" channel and the sweep channel is the "Bias".

Adds the parameters `"KPFM:Bias"`, `"KPFM:Frequency Shift"`, `"KPFM:Residuals AbsSum"` and the channels `"KPFM:Fit"`, `"KPFM:Residuals"` to the SpmGrid `grid`.

If `bwd` is `true` (default), the plot will include data from backward sweep as well (if they exist).
