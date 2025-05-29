```
draw_yaxis(y::Real; opts...)
```

`draw_yaxis(y)` draws a thin arrow from the origin to `(0,y)`.

`draw_yaxis(y1,y2)` is equivalent to `draw_yaxis(x1); draw_yaxis(x2)`.

If no y-value is given, draw a pair of arrows from the origin  to values 10% larger than those returned by `ylims()`.
