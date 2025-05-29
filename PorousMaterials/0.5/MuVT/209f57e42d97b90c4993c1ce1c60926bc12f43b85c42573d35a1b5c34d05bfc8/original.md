```
results, molecules = μVT_sim(xtal, molecule_templates, temperature, pressure,
                             ljff; molecules=Array{Molecule, 1}[], settings=settings)
```

Runs a grand-canonical (μVT) Monte Carlo simulation of the adsorption of a molecule in a xtal at a particular temperature and pressure using a Lennard Jones force field.

Markov chain Monte Carlo moves include:

  * deletion/insertion
  * translation
  * reinsertion
  * identity change (if multiple components) [see here](http://dx.doi.org/10.1080/00268978800100743)

Translation stepsize is dynamically updated during burn cycles so that acceptance rate of translations is ~0.4.

A cycle is defined as max(20, number of adsorbates currently in the system) Markov chain proposals.

# Arguments

  * `xtal::Crystal`: the porous xtal in which we seek to simulate adsorption
  * `molecule_templates::Array{Molecule, 1}`: an array of the templates of unique adsorbate molecules of which we seek to simulate
  * `temperature::Float64`: temperature of bulk gas phase in equilibrium with adsorbed phase in the porous material. units: Kelvin (K)
  * `pressures::Array{Float64, 1}`: pressure of bulk gas phase in equilibrium with adsorbed phase in the porous material for each adsorbate. units: bar the adsorption
  * `ljff::LJForceField`: the molecular model used to describe the
  * `molecules::Array{Array{Molecule{Cart}, 1}, 1}`: a starting configuration of molecules in the xtal with an array per species.
  * `n_cycles_per_volume::Int`: the number of MC cycles per volume, split evenly between `n_burn_cycles` and `'n_sample_cycles`, where
  * `fraction_burn_cycles::Float64`: the proportion of the MC cycles to burn before sampling
  * `sample_frequency::Int`: during the sampling cycles, sample e.g. the number of adsorbed gas molecules every this number of Markov proposals
  * `verbose::Bool`: whether or not to print off information during the simulation
  * `ewald_precision::Float64`: desired precision for the long range Ewald summation
  * `eos::Symbol`: equation of state to use for calculation of fugacity from pressure
  * `write_adsorbate_snapshots::Bool`: whether the simulation will create and save a snapshot file
  * `snapshot_frequency::Int`: the number of cycles taken between each snapshot (after burn cycle completion)
  * `calculate_density_grid::Bool`: whether the simulation will keep track of a density grid for adsorbates
  * `density_grid_dx::Float64`: The (approximate) space between voxels (in Angstroms) in the density grid. The number of voxels in the simulation box is computed automatically by [`required_n_pts`](@ref).
  * `density_grid_molecular_species::Symbol`: the adsorbate for which we will make a density grid of its position (center).
  * `density_grid_sim_box::Bool`: `true` if we wish for the density grid to be over the entire simulation box as opposed to the box of the crystal passed in. `false` if we wish the density grid to be over the original `xtal.box`, before replication, passed in.
  * `autosave::Bool`: `true` if we wish to automatically save the simulation results to the standard path/filename.
  * `results_filename_comment::AbstractString`: An optional comment that will be appended to the name of the saved file (if autosaved)
