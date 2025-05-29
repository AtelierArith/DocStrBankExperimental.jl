```
calculate_mutual_capacitance(sim::Simulation, ij::Tuple{Int, Int}; consider_multiplicity::Bool = true)
```

Returns the mutual capacitance between the contacts with ID `i = ij[1]` and `j = ij[2]`. It is calculated via the weighting potentials of the contacts, $\Phi_i^w(\vec{r})$ and $\Phi_j^w(\vec{r})$:

$$
c_{ij} = \epsilon_0 \int_{World} \nabla \Phi_i^w(\vec{r}) ϵ_r(\vec{r}) \nabla \Phi_j^w(\vec{r}) d\vec{r}
$$

!!! note
    These are elements of the Mawell Capcitance Matrix. Look up [Capacitances](@ref) for more information.


!!! note
    The electric potential as well as the two weighting potentials of both contacts have to be calculated.


## Arguments

  * `sim::Simulation`: [`Simulation`](@ref) for which the capacitance matrix is calculated.
  * `ij::Tuple{Int,Int}`: Tuple of indices of the contacts for which the capacitance should be calculated.

## Keywords

  * `consider_multiplicity::Bool = true`: Whether symmetries of the system should be taken into account.    For example, in case of true coaxial detector center around the origin and calculated on a cartesian grid    with the `x-axis` going from `[0, x_max]` and the `y-axis` going from `[0, y_max]` the multiplicity is 4   and, if `consider_multiplicity == true`, the returned value is already multiplied by 4.
