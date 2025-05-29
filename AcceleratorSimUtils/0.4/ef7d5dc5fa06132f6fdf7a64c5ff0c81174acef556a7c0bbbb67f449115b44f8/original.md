```
calc_pc(mass; E_tot = nothing, β = nothing, E_kinetic = nothing, γ = nothing) -> pc
calc_pc(species; E_tot = nothing, β = nothing, E_kinetic = nothing, γ = nothing) -> pc
```

Returns the particle momentum*c (in `eV`) given one of `E_tot` (total energy), `β` (velocity/c),  `E_kinetic` (kinetic energy), or `γ` (relativistic factor).  One and only one of the optional arguments `E_tot`, `β`, `E_kinetic`, or `γ` should be set. All arguments are `Numbers` except `species` which is of type `Species`.

The `mass` argument is in units of `energy/c^2`.

Also see the functions `calc_E_tot`, `calc_β`, `calc_β1`, `calc_E_kinetic`, and `calc_γ`
