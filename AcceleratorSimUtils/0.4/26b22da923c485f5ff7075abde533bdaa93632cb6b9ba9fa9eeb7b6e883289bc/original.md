```
calc_changed_energy(mass; old_pc, dE) -> (pc, E_tot)
calc_changed_energy(species::Species; old_pc, dE) -> (pc, E_tot)
```

Given an initial `old_pc` particle `momentum*c`, and a change in energy `dE`, calculate the final `momentum*c` and total energy. If `dE` is too large and negative for there to be a solution, `nothing, nothing` is returned. All arguments are `Numbers` except `species` which is of type `Species`.

The `mass` argument is in units of `energy/c^2`.

The calculation is done in such a way as to not loose precision.
