```
calc_β(mass; E_tot = nothing, pc = nothing, E_kinetic = nothing, γ = nothing) -> β
calc_β(species; E_tot = nothing, pc = nothing, E_kinetic = nothing, γ = nothing) -> β
```

Returns the normalized velocity `β` = `v/c` of a particle given one of `E_tot` (total energy),  `pc` (momentum*c), `E_kinetic` (kinetic energy), or `γ` (relativistic factor).  One and only one of the optional arguments `E_tot`, `pc`, `E_kinetic`, or `γ` should be set. All arguments are `Numbers` except `species` which is of type `Species`.

The `mass` argument is in units of `energy/c^2`.

Also see the functions `calc_E_tot`, `calc_pc`, `calc_β1`, `calc_E_kinetic`, and `calc_γ`
