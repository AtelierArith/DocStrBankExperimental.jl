Helper type for rendering arrows in the visualizer.

Usage:

Given a `Visualizer` named `vis`, we can create an arrow with:

```
ArrowVisualizer arrow(vis)
setobject!(arrow)
```

We can then set the base and direction of the arrow with:

```
settransform!(arrow, Point(0.0, 0.0, 0.0), Vec(0.5, 0.5, 0.0))
```

Note that this `settransform!` should work correctly inside an `Animation`, as long as you do `setobject!` before starting the animation.
