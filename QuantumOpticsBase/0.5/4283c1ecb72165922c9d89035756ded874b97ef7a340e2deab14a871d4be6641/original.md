```
fermionstates([T, ]Nmodes, Nparticles)
fermionstates([T, ]b, Nparticles)
```

Generate all fermionic occupation states for N-particles in M-modes. `Nparticles` can be a vector to define a Hilbert space with variable particle number. `T` is the type of the occupation states - default is `OccupationNumbers{FermionStatistics,Int}`, but can be any occupations type.
