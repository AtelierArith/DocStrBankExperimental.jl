```
calc_E_tot(mass; pc = nothing, β = nothing, E_kinetic = nothing, γ = nothing) -> E_tot
calc_E_tot(species; pc = nothing, β = nothing, E_kinetic = nothing, γ = nothing) -> E_tot
```

Returns the total energy of a particle (in `eV`) given one of `pc` (momentum*c), `β` (velocity/c),  `E_kinetic` (kinetic energy), or `γ` (relativistic factor). One and only one of the optional arguments `pc`, `β`, `E_kinetic`, or `γ` should be set. All arguments are `Numbers` except `species` which is of type `Species`.

The `mass` argument is in units of `energy/c^2`.

Also see the functions `calc_pc`, `calc_β`, `calc_β1`, `calc_E_kinetic`, and `calc_γ`
