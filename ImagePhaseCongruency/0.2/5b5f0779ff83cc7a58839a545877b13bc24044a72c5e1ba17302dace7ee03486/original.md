Generate grid for constructing frequency domain filters.

```
Usage:  f = filtergrid(rows, cols)
        f = filtergrid((rows, cols))

Arguments:  rows, cols - Size of image/filter

Returns:             f - Grid of size (rows, cols) containing normalised
                         frequency values from 0 to 0.5.  Grid is quadrant
                         shifted so that 0 frequency is at f[1,1]

```

Used by [`phasecongmono`](@ref), [`phasecong3`](@ref), etc etc

See also: [`filtergrids`](@ref)   if you also want normalized frequency grids in           the x and y directions as well.
