```
update_density!(grid, molecule, species)
```

updates the density grid based on an array of molecules. If a molecule doesn't match the specified species it won't be added to the density grid. This function doesn't calculate the actual densities, it will need a `./ = num_snapshots` at the end of the GCMC simulation.

# Arguments

  * `grid::Grid`: the grid to be updated
  * `molecules::Array{Molecule, 1}`: An array of molecules whose positions will be added to the grid
  * `species::Symbol`: The species of atom that can be added to this density grid
