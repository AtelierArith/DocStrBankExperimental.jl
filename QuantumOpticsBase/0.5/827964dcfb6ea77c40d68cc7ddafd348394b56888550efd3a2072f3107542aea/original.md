```
bosonstates([T, ]Nmodes, Nparticles)
bosonstates([T, ]b, Nparticles)
```

Generate all bosonic occupation states for N-particles in M-modes. `Nparticles` can be a vector to define a Hilbert space with variable particle number. `T` is the type of the occupation states - default is `OccupationNumbers{BosonStatistics,Int}`, but can be any occupations type.
