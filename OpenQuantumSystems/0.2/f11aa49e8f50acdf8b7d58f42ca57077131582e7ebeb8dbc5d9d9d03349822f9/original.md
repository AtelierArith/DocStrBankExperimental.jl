```
getMolStateFC(mol, molElState1, molVibState1, molElState2, molVibState2)
```

Get the energy of the [`Molecule`](@ref) state.

# Arguments

  * `mol`: Instance of [`Molecule`](@ref).
  * `molElState1`, `molElState2`: Electric state of the molecule in local basis (i.e. 1 or 2, where 1 is ground state).
  * `molVibState1`, `molVibState2`: Vibrational state of the molecule (e.g. [1, 5, 2, 2]).
