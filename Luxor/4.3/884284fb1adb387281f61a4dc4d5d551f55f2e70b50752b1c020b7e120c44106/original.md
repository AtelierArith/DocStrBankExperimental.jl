```
crescent(pos, innerradius, outeradius;
    action=nothing,
    vertices=false,
    reversepath=false,
    steps = 30)
```

Create a crescent-shaped polygon, aligned with the current x-axis, and add it to the current path. If the inner radius is 0, you'll get a semicircle.

See also `crescent(pos1, innerradius, pos2, outeradius...)`.

## Examples

Create a filled crescent shape with outer radius of 200, inner radius of 130.

```julia
crescent(O, 130, 200, :fill) # or
crescent(O, 130, 200, action=:fill)
```

Create a stroked crescent shape - the inner radius of 0 produces a semicircle - and add it to the current path.

```julia
crescent(O, 0, 200, :stroke) # or
crescent(O, 0, 200, action=:stroke)
```
