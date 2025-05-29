```
star(center, radius, npoints, ratio=0.5, orientation, action=:none;
    vertices = false, reversepath=false)
star(center, radius, npoints, ratio=0.5, orientation=0.0;
    action=:none, vertices = false, reversepath=false)
```

Make a star centered at `center` with `npoints` sections oriented by `orientation`. `ratio` specifies the height of the smaller radius of the star relative to the larger.

Returns the vertices of the star.

Use `vertices=true` to only return the vertices of a star instead of making it.

## Examples

```julia
star(O, 120, 5, 0.5, 0.0, :fill,
    vertices = false,
    reversepath=false)
```

```julia
star(O, 220, 5, 0.5;
    action=:stroke,
    vertices = false,
    reversepath=false)
```
