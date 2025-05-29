```
offsetpoly(plist, shape::Function)
```

Return a closed polygon that is offset from and encloses an polyline.

The incoming set of points `plist` is treated as an polyline, and another set of points is created, which form a closed polygon offset from the source poly.

There must be at least 4 points in the polyline.

This method for `offsetpoly()` treats the list of points as `n` vertices connected with `n - 1` lines. (The other method `offsetpoly(plist, d)` treats the list of points as `n` vertices connected with `n` lines.)

The supplied function determines the width of the line. `f(0, θ)` gives the width at the start (the slope of the curve at that point is supplied in θ), `f(1, θ)` provides the width at the end, and `f(n, θ)` is the width of point `n/l`.

# Examples

This example draws a tilde, with the ends starting at 20 (10 + 10) units wide, swelling to 50 (10 + 10 + 15 + 15) in the middle, as f(0.5) = 25.

```julia
f(x, θ) = 10 + 15sin(x * π)
sinecurve = [Point(50x, 50sin(x)) for x in (-π):(π / 24):π]
pgon = offsetpoly(sinecurve, f)
poly(pgon, :fill)
```

This example enhances the vertical part of the curve, and thins the horizontal parts.

```julia
g(x, θ) = rescale(abs(sin(θ)), 0, 1, 0.1, 30)
sinecurve = [Point(50x, 50sin(x)) for x in (-π):(π / 24):π]
pgon = offsetpoly(sinecurve, g)
poly(pgon, :fill)
```

TODO - rewrite it!
