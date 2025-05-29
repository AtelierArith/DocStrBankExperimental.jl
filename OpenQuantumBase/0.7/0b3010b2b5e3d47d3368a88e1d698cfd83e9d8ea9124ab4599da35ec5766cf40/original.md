```
function AdiabaticFrameHamiltonian(ωfuns, geofuns)
```

Constructor of adiabatic frame Hamiltonian. `ωfuns` is a 1-D array of functions which specify the eigen energies (in `GHz`) of the Hamiltonian. `geofuns` is a 1-D array of functions which specifies the geometric phases of the Hamiltonian. `geofuns` can be thought as a flattened lower triangular matrix (without diagonal elements) in column-major order.
