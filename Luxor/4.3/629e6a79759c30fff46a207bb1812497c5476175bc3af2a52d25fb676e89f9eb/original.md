```
easeinoutbezier(t, b, c, d, cpt1, cpt2)
```

This easing function takes six arguments, the usual `t`, `b`, `c`, and `d`, but also two points. These are the normalized control points of a Bezier curve drawn between `Point(0, 0)` to `Point(1.0, 1.0)`. The `y` value of the Bezier is the eased value for `t`.

In your `frame()` generating function, if a Scene specifies the `easeinoutbezier` easing function, you can use this:

```julia
...
lineareasing = rescale(framenumber, 1, scene.framerange.stop)
beziereasing = scene.easingfunction(lineareasing, 0, 1, 1,
    Point(0.25, 0.25), Point(0.75, 0.75))
...
```

These two control points lie on the line between `0/0` and `1/1`, so it's equivalent to a linear easing (`lineartween()` or `easingflat`).

However, in the next example, the two control points define a wave-like curve that changes direction before changing back. When animating with this easing function, an object will 'go retrograde' for a while.

```julia
lineareasing = rescale(framenumber, 1, scene.framerange.stop)
beziereasing = scene.easingfunction(lineareasing, 0, 1, 1,
    Point(0.01, 1.99), Point(0.99, -1.5))
```
