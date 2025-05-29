```
matrixelement(ion::Ion, transition::Tuple, I::Real, ϵhat::NamedTuple, khat::NamedTuple, Bhat::NamedTuple=(;z=1))
```

Computes the matrix elements (units of Hz) between two energy sublevels **args**

  * `ion`: Ion undergoing transition
  * `transition`: Tuple of sublevels (full names or aliases) between which the transition is being calculated. Must be formatted such that `energy(transition[2]) > energy(transition[1])`
  * `I`: Intensity of the driving field
  * `ϵhat`: Unit vector of light polarization
  * `khat`: Unit vector of light wavevector
  * `Bhat`: Unit vector of magnetic field
