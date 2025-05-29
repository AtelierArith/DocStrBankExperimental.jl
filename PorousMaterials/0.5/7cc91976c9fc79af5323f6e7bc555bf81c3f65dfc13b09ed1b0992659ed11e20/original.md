gg*energy = vdw*energy(molecule*id, molecules, ljforcefield, simulation*box)

Calculates van der Waals interaction energy of a single adsorbate `molecules[molecule_id]` with all of the other molecules in the system. Periodic boundary conditions are applied, using the nearest image convention.

# Arguments

  * `molecule_id::Int`: Molecule ID used to determine which molecule in `molecules` we wish to calculate the guest-guest interactions
  * `molecules::Array{Molecule, 1}`: An array of Molecule data structures
  * `ljforcefield::LJForceField`: A Lennard Jones forcefield data structure describing the interactions between different atoms
  * `simulation_box::Box`: The simulation box for the computation.

# Returns

  * `gg_energy::Float64`: The guest-guest interaction energy of `molecules[molecule_id]` with the other molecules in `molecules`
