```
ParaboloidSurface(apex, radius, focallength)
```

A paraboloid surface embedded in R³ and extending up to a distance `radius` from its focal axis, which is aligned along the z direction and passes through `apex` (the apex of the paraboloid). The equation of the paraboloid is the following:

$$
f(x, y) = \frac{(x - x_0)^2 + (y - y_0)^2}{4f} + z_0\qquad\text{for } x^2 + y^2 < r^2,
$$

where $(x_0, y_0, z_0)$ is the apex of the parabola, $f$ is the focal length, and $r$ is the clip radius.

```
ParaboloidSurface(apex, radius)
```

This creates a paraboloid surface with focal length equal to 1.

```
ParaboloidSurface(apex)
```

This creates a paraboloid surface with focal length equal to 1 and a rim with unit radius.

```
ParaboloidSurface()
```

Same as above, but here the apex is at `Apex(0, 0, 0)`.

See also [https://en.wikipedia.org/wiki/Paraboloid](https://en.wikipedia.org/wiki/Paraboloid).
