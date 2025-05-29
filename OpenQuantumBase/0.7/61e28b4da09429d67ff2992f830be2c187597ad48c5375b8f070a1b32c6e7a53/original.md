```julia
struct DiffEqLiouvillian{diagonalization, adiabatic_frame}
```

Defines a total Liouvillian to feed to the solver using the `DiffEqOperator`  interface. It contains both closed-system and open-system Liouvillians.

# Fields

  * `H`: Hamiltonian
  * `opensys_eig`: Open system in eigenbasis
  * `opensys`: Open system in normal basis
  * `lvl`: Levels to truncate
  * `digits`: Number of digits to round for zero gap value
  * `sigdigits`: Number of significant digits to round for gaps
  * `u_cache`: Internal cache
