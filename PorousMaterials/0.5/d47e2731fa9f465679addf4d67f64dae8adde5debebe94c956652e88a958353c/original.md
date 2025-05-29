```
write_cube(grid, filename, verbose=true)
```

Write grid to a .cube file format. This format is described here: http://paulbourke.net/dataformats/cube/ The atoms of the unit cell are not printed in the .cube. Instead, use .xyz files to also visualize atoms.

# Arguments

  * `grid::Grid`: grid with associated data at each grid point.
  * `filename::AbstractString`: name of .cube file to which we write the grid; this is relative to `rc[:paths][:grids]`.
  * `verbose::Bool`: print name of file after writing.
  * `length_units::String`: units for length. Bohr or Angstrom.
