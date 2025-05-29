```
draw_ytick(y::Real, len = _DEFAULT_TICK_LEN; opts...)
```

`draw_ytick(y::Real,len)` draws a tick mark on the y-axis with total length `len`. If `len` is omitted, use `SimpleDrawing._DEFAULT_TICK_LEN`.

`draw_xtick(ylist,len)` calls `draw_ytick` for each value in `xyist`.
