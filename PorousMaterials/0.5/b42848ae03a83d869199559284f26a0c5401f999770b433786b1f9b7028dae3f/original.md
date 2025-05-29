```
write_xyz(box, molecules, xyz_file)
```

Writes the coordinates of all atoms in molecules to the given xyz_file file object passing a file object around is faster for simulation because it can be opened once at the beginning of the simulation and closed at the end.

This writes the coordinates of the molecules in cartesian coordinates, so the box is needed for the conversion.

# Arguments

  * `box::Box`: The box the molecules are in, to convert molecule positions to cartesian coordinates
  * `molecules::Array{Array{Molecule{Frac}, 1}, 1}`: The array containing arrays of molecules, separated by species, to be written to the file
  * `xyz_file::IOStream`: The open 'write' file stream the data will be saved to
