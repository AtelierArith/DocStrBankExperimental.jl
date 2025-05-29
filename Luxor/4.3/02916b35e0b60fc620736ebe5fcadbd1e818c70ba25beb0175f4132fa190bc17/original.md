```
crescent(cp1, r1, cp2, r2;
    action=nothing,
    vertices=false,
    reversepath=false)
```

Create a crescent-shaped polygon, aligned with the current x-axis, by finding the intersection of two circles, and add it to the current path. The two center positions should be different.

See also `crescent(point, innerradius, outeradius...)`.

## Examples

Create a filled crescent shape from two circles.

```julia
crescent(O, 100, O + (60, 0), 150, :fill) # or
crescent(O, 100, O + (60, 0), 150, action=:fill)
```
