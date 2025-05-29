```
calc_E_kinetic(mass; E_tot = nothing, pc = nothing, β = nothing, γ = nothing) -> E_kinetic
calc_E_kinetic(species; E_tot = nothing, pc = nothing, β = nothing, γ = nothing) -> E_kinetic
```

Returns the kinetic energy of a particle in `eV` given one of `E_tot` (total energy),  `pc` (momentum*c), `β` (velocity/c), or `γ` (relativistic factor). One and only one of the optional arguments `E_tot`, `pc`, `β`, or `γ` should be set.

All arguments are `Numbers` except `species` which is of type `Species`. The `mass` argument is in units of `energy/c^2`.

Also see the functions  `calc_E_tot`; `calc_pc`, `calc_β`, `calc_β1`, and `calc_γ`
