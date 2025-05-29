```
MISTBCGrid(grid::AbstractString)
```

Load and return the MIST bolometric corrections for the given photometric system `grid`. This type is used to create instances of [`MISTBCTable`](@ref) that have fixed dependent grid variables ([Fe/H], Av, Rv). This can be done either by calling an instance of `MISTBCGrid` with `(feh, Av)` arguments or by using the appropriate constructor for [`MISTBCTable`](@ref).

```jldoctest
julia> grid = MISTBCGrid("JWST")
MIST bolometric correction grid for photometric system MIST_JWST

julia> grid(-1.01, 0.11) # Can be called to construct table with interpolated [Fe/H], Av
MIST bolometric correction table with [Fe/H] -1.01 and V-band extinction 0.11
```
