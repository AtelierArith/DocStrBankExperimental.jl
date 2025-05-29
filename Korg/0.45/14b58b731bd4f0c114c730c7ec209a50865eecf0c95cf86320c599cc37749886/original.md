```
merge_close_lines(linelist; merge_distance=0.2)
```

Produce a list of the species and wavelengths of the lines in `linelist`, merging lines of the same species that are within `merge_distance` (default: 0.2 Å).  This is useful for labeling lines in a plot after running [`prune_linelist`](@ref).

# Arguments

  * `linelist`: the linelist (a vector of `Line` objects)

# Keyword Arguments

  * `merge_distance=0.2`: The maximum distance in Å between lines of the same species to be merged into a single entry

# Returns

A vector of tuples `(wl, wl_low, wl_high, species)` where `wl` is gf-weighted wavelength of each set of merged lines (Å), `wl_low` and `wl_high` are their highest and lowest wavelength, and `species` is a string (not a `Korg.Species`) identifying the species of the line. These will be in wavelength order.
