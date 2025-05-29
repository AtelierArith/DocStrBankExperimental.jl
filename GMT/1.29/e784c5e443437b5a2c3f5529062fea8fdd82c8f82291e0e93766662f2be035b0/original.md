```
grdtrack(cmd0::String="", arg1=nothing, arg2=nothing; kwargs...)
```

Interpolates the grid(s) at the positions in the table and returns the table with the interpolated values added as (one or more) new columns.

When using two numeric inputs and no G option, the order of the x,y and grid is not important. That is, both of this will work: $D = grdtrack([0 0], Grid);$  or  $D = grdtrack(Grid, [0 0]);$ 

To see the documentation, type: $@? grdtrack$
