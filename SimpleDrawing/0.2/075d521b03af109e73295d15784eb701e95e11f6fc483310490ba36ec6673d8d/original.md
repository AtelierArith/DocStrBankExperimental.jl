```
draw_xtick(x::Real, len = _DEFAULT_TICK_LEN; opts...)
```

`draw_xtick(x::Real,len)` draws a tick mark on the x-axis with total length `len`. If `len` is omitted, use `SimpleDrawing._DEFAULT_TICK_LEN`.

`draw_xtick(xlist,len)` calls `draw_xtick` for each value in `xlist`.
