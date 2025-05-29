```
unzip(vs)
unzip(v1, v2, ...)
unzip(r::Function, a, b)
```

Take a vector of points described by vectors (as returned by, say `r(t)=[sin(t),cos(t)], r.([1,2,3])`, and return a tuple of collected x values, y values, and optionally z values.

Wrapper around the `invert` function of `SplitApplyCombine`.

If the argument is specified as a comma separated collection of vectors, then these are combined and passed along.

If the argument is a function and two end points, then the function is evaluated at points between `a` and `b`; for the univaraite case, the  points are chosen adaptively.

This is useful for plotting when the data is more conveniently represented in terms of vectors, but the plotting interface requires the x and y values collected.

Examples:

```
using Plots
r(t) = [sin(t), cos(t)]
rp(t) = [cos(t), -sin(t)]
plot(unzip(r, 0, 2pi)...)  # calls plot(xs, ys)

t0, t1 = pi/6, pi/4

p, v = r(t0), rp(t0)
plot!(unzip(p, p+v)...)  # connect p to p+v with line

p, v = r(t1), rp(t1)
quiver!(unzip([p])..., quiver=unzip([v]))
```

Based on `unzip` from the `Plots` package. Implemented through `invert` of `SplitApplyCombine`

Note: for a vector of points, `xs`, each of length `2`, a similar functionality would be `(first.(xs), last.(xs))`. If each point had length `3`, then with `second(x)=x[2]`, a similar functionality would be `(first.(xs), second.(xs), last.(xs))`.

```
