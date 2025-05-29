```
ngon(centerpos, radius, sides=5, orientation=0;
    action=:none,
    vertices=false,
    reversepath=false)
```

Draw a regular polygon centered at point `centerpos`.

Find the vertices of a regular n-sided polygon centered at `x`, `y` with circumradius `radius`.

The polygon is constructed counterclockwise, starting with the first vertex drawn below the positive x-axis.

If you just want the raw points, use keyword argument `vertices=true`, which returns the array of points. Compare:

```julia
julia> ngon(0, 0, 4, 4, 0, vertices=true) # returns the polygon's points:
4-element Vector{Point}:
 Point(2.4492935982947064e-16, 4.0)
 Point(-4.0, 4.898587196589413e-16)
 Point(-7.347880794884119e-16, -4.0)
 Point(4.0, -9.797174393178826e-16)
```

whereas

```julia
ngon(0, 0, 4, 4, 0, :close) # draws a polygon
```
