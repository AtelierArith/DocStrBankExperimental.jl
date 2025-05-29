```
molecule = Molecule(species, check_neutrality=true)
```

construt a `Molecule` from input files read from `joinpath(rc[:paths][:molecules], species)`

center of mass assigned using atomic masses from `rc[:atomic_masses]`.

# Arguments

  * `species::String`: name of the molecule
  * `check_neutrality::Bool`: assert the molecule is charge neutral for safety.

# Returns

  * `molecule::Molecule{Cart}`: a molecule in Cartesian coordinates
