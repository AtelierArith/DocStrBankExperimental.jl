```
draw_curve(pts::Array{Complex{T},1}, closed::Bool = true; opts...) where {T}
```

`draw_curve(plist)` draws a closed curve through points in the `plist` which is a 1-dimensional list of complex numbers. Use `draw_curve(plist,false)` for an open curve.
