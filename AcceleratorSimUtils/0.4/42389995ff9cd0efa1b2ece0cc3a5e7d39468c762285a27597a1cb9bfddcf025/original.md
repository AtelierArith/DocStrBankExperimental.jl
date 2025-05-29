```
calc_1β(mass; E_tot = nothing, pc = nothing, E_kinetic = nothing, γ = nothing) -> 1-β
calc_1β(species; E_tot = nothing, pc = nothing, E_kinetic = nothing, γ = nothing) -> 1-β
```

Returns the quantity `1 - β` = `1 - v/c` of a particle given one of `E_tot` (total energy),  `pc` (momentum*c), `E_kinetic` (kinetic energy), or `γ` (relativistic factor).  In the high energy limit, this is approximately `1/(2γ^2)`. `calc_1β` is computed such that in the high energy limit, round off error is not a problem.

One and only one of the optional arguments `E_tot`, `pc`, `E_kinetic`, or `γ` should be set. All arguments are `Numbers` except `species` which is of type `Species`. The `mass` argument is in units of `energy/c^2`.

Also see the functions `calc_E_tot`; `calc_pc`, `calc_β`, `calc_E_kinetic`, and `calc_γ`
