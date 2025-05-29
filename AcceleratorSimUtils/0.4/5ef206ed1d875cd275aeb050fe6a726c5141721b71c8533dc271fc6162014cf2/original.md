```
calc_γ(mass; E_tot = nothing, pc = nothing, β = nothing, E_kinetic = nothing) -> γ
calc_γ(species; E_tot = nothing, pc = nothing, β = nothing, E_kinetic = nothing) -> γ
```

Returns the relativistic gamma factor of a particle given `E_tot` (total energy),  `pc` (momentum*c), `β` (velocity/c), or `E_kinetic` (kinetic energy).  One and only one of the optional arguments `E_tot`, `pc`, `β`, or `E_kinetic` should be set.

All arguments are `Numbers` except `species` which is of type `Species`. The `mass` argument is in units of `energy/c^2`.

Also see the functions `calc_pc`, `calc_β`, `calc_β1`, `calc_E_kinetic`, and `calc_γ`
