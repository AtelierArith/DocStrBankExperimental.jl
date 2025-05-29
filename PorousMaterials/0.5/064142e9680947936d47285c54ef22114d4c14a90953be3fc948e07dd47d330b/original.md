```
save_name = henry_result_savename(crystal, molecule, temperature,
                               ljforcefield, insertions_per_volume;
                               comment="")
```

Determine the name of files saved while calculating the henry coefficient. It uses many pieces of information from the simulation to ensure the file name accurately describes what it holds.

# Arguments

  * `crystal::Crystal`: The porous crystal being tested
  * `molecule::Molecule`: The molecule being tested inside the crystal
  * `temperature::Float64`: The temperature used in the simulation units: Kelvin (K)
  * `ljforcefield::LJForceField`: The molecular model being used in the simulation to describe the intermolecular Van der Waals forces
  * `insertions_per_volume::Union{Int, Float64}`: The number of widom insertions per unit volume. Will be scaled according to the crystal we're working with
  * `comment::AbstractString`: An optional comment that will be appended to the filename
