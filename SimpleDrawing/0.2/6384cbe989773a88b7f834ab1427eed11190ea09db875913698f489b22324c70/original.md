```
draw_xaxis(x::Real; opts...)
```

`draw_xaxis(x)` draws a thin arrow from the origin to `(x,0)`.

`draw_xaxis(x1,x2)` is equivalent to `draw_xaxis(x1); draw_xaxis(x2)`.

If no x-value is given, draw a pair of arrows from the origin  to values 10% larger than those returned by `xlims()`.
