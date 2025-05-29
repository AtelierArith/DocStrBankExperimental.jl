```
ASECalculator(; <keyword arguments>)
```

A Python [ASE](https://wiki.fysik.dtu.dk/ase) calculator.

This calculator is only available when PythonCall is imported. It is the user's responsibility to have the required Python packages installed. This includes ASE and any packages providing the calculator.

Contrary to the rest of Molly, unitless quantities are assumed to have ASE units: Å for length, eV for energy, u for mass, and Å sqrt(u/eV) for time. Unitful quantities will be converted as appropriate.

Not currently compatible with [`TriclinicBoundary`](@ref).

# Arguments

  * `ase_calc`: the ASE calculator created with PythonCall.
  * `atoms`: the atoms, or atom equivalents, in the system.
  * `coords`: the coordinates of the atoms in the system. Typically a   vector of `SVector`s of 2 or 3 dimensions.
  * `boundary`: the bounding box in which the simulation takes place.
  * `elements=nothing`: vector of atom elements as a string, either `elements` or   `atoms_data` (which contains element data) must be provided.
  * `atoms_data=nothing`: other data associated with the atoms.
  * `velocities=nothing`: the velocities of the atoms in the system, only required   if the velocities contribute to the potential energy or forces.
