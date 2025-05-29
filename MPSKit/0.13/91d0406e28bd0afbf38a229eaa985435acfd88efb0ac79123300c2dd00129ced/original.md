```
open_boundary_conditions(mpo::InfiniteMPOHamiltonian, L::Int) -> FiniteMPOHamiltonian
```

Convert an infinite MPO into a finite MPO of length `L`, by applying open boundary conditions.
