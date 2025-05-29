```julia
Invisible(x, y)

```

Create an invisible object with the sole function of extending coordinate bounds to `x, y`, which should be `Interval`s or `nothing`.

You can also use `Invisible(bounds_xy(object)...)` to extend bounds to those in `object`, or `Invisible(bounds_xy(object)[1], nothing)` to extend only the `x` axes, etc.
