```
accessibility_grid, nb_segments_blocked, porosity = compute_accessibility_grid(crystal,
probe_molecule, ljforcefield; resolution::Union{Float64, Tuple{Int, Int, Int}}=1.0, energy_tol=10.0, energy_unit=:kJ_mol,
verbose=true, write_b4_after_grids=false, block_inaccessible_pockets=true)
```

Overlay a grid of points about the unit cell. Compute the potential energy of a probe molecule at each point. If the potential energy is less than `energy_tol`, the grid point is declared as accessible to an adsorbate; otherwise inaccessible.

If `block_pockets` is true: Then perform a flood fill algorithm to label disparate (unconnected) segments in the grid.

Then build a graph whose vertices are the unconnected segments in the flood-filled grid and whose edges are the connections between the segments across the periodic boundary.

Then find any simple cycles in the grid. Any vertex that is involved in a simple cycle is considered accessible since a molecule can travel from that segment in the home unit cell to the same segment but in a different unit cell. If any vertex is not involved in a cycle, the segment is declared as inaccessible and all grid points in this segment are re-labeled as inaccessible.

Returns `accessibility_grid::Grid{Bool}` and `nb_segments_blocked`, the latter the number of segments that were blocked because they were determined to be inaccessible.

# Arguments

  * `crystal::Crystal`: the crystal for which we seek to compute an accessibility grid.
  * `probe_molecule::Molecule` a molecule serving as a probe to determine whether a given point can be occupied and accessed.
  * `LJForceField::LJForceField`: the force field used to compute the potential energy of the probe molecule
  *   * `resolution::Union{Float64, Tuple{Int, Int, Int}}=1.0`: maximum distance between grid points, in Å, or a tuple specifying the number of grid points in each dimension.
  * `energy_tol::Float64`: if the computed potential energy is less than this, we declare the grid point to be occupiable. Also this is the energy barrier beyond which we assume the probe adsorbate cannot pass. Units given by `energy_units` argument
  * `energy_units::Symbol`: units of energy (`:kJ_mol` or `:K`) to be used in determining threshold for occupiability and whether molecule can percolate over barrier in channel. (see `energy_tol`)
  * `write_b4_after_grids::Bool`: write a .cube file of occupiability for visualization both before and after flood fill/blocking inaccessible pockets
