```
xf₀ = find_energy_minimum_gridsearch(xtal, molecule, ljff; resolution=(50, 50, 50))
```

perform an [`energy_grid`](@ref) calculation and, via a grid search, find the minimum energy position of a molecule.

# Arguments

  * `xtal::Crystal`: The crystal being investigated
  * `molecule::Molecule{Cart}`: The molecule used to probe energy surface
  * `ljff::LJForceField`: The force field used to calculate interaction energies
  * `resolution::Union{Float64, Tuple{Int, Int, Int}}=1.0`: maximum distance between grid points, in Å, or a tuple specifying the number of grid points in each dimension.

# Returns

  * `minimized_molecule::Molecule{Frac}`: the molecule at its minimum energy position
  * `min_energy::Float64`: the associated minimum molecule-crystal interaciton energy (kJ/mol)
