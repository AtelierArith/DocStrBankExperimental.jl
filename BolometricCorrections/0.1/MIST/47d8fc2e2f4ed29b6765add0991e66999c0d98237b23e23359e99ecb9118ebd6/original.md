```
MISTBCTable(grid::MISTBCGrid, feh::Real, Av::Real)
```

Interpolates the MIST bolometric corrections in `grid` to a fixed value of [Fe/H] (`feh`) and V-band extinction (`Av`), leaving only `Teff` and `logg` as dependent variables (the MIST BCs have only one `Rv` value). Returns an instance that is callable with arguments `(Teff, logg)` to interpolate the bolometric corrections as a function of temperature and surface gravity.

```jldoctest
julia> grid = MISTBCGrid("JWST")
MIST bolometric correction grid for photometric system MIST_JWST

julia> table = MISTBCTable(grid, -1.01, 0.011)
MIST bolometric correction table with [Fe/H] -1.01 and V-band extinction 0.011

julia> length(table(2755, 0.01)) == 29 # Returns BC in each filter
true
```
