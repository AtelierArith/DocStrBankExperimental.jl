```
grid = energy_grid(crystal, molecule, ljforcefield; resolution=1.0, temperature=298.0, n_rotations=750)
```

Superimposes a regular grid of points (regularly spaced in fractional coordinates of the `crystal.box`) over the unit cell of a crystal, with `n_gridpts` dictating the number of grid points in the a, b, c directions (including 0 and 1 fractional coords). The fractional coordinates 0 and 1 are included in the grid, although they are redundant. Then, at each grid point, calculate the ensemble average potential energy of the molecule when its mass is centered at that point. The average is taken over Boltzmann-weighted rotations.

The ensemble average is a Boltzmann average over rotations:  - R T log ⟨e⁻ᵇᵁ⟩

# Arguments

  * `crystal::Crystal`: crystal in which we seek to compute an energy grid for a molecule. `grid.box` will be `framework.box`.
  * `molecule::Molecule`: molecule for which we seek an energy grid
  * `ljforcefield::LJForceField`: molecular model for computing molecule-crystal interactions
  * `resolution::Union{Float64, Tuple{Int, Int, Int}}=1.0`: maximum distance between grid points, in Å, or a tuple specifying the number of grid points in each dimension.
  * `n_rotations::Int`: number of random rotations to conduct in a Monte Carlo simulation for finding the free energy of a molecule centered at a given grid point. This is only relevant for molecules that are comprised of more than one Lennard Jones sphere.
  * `temperature::Float64`: the temperature at which to compute the free energy for molecules where rotations are required. Lower temperatures overemphasize the minimum potential energy rotational conformation at that point.
  * `units::Symbol`: either `:K` or `:kJ_mol`, the units in which the energy should be stored in the returned `Grid`.
  * `center::Bool`: shift coords of grid so that the origin is the center of the unit cell `crystal.box`.
  * `verbose::Bool=true`: print some information.

# Returns

  * `grid::Grid`: A grid data structure containing the potential energy of the system
