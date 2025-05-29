```
outer_surface_of_solid(fens, bdry_fes)
```

Find the finite elements that form the outer boundary surface.

!!! note:

The code will currently not work correctly for 2D axially symmetric geometries.

# Return

Set of boundary finite elements that enclose the solid. Now cavities  are included.
