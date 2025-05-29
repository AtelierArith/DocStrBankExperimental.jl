```
bfacemask!(grid::ExtendableGrid,
                maskmin,
                maskmax,
                ireg;
                allow_new=true,
                tol=1.0e-10)
```

Edit region numbers of grid  boundary facets  via rectangular mask. If `allow_new` is true (default), new facets are added.

ireg may be an integer  or a function `ireg(current_region)`.

A zero region number removes boundary faces.

Examples: [Rectangle-with-multiple-regions](@ref)
