```
mesh_psi_spacing(
    dd::IMAS.dd;
    eq_time_idx::Int=1,
    eq_profiles_2d_idx::Int=1,
    grid_ggd_idx::Int=1,
    space_idx::Int=1,
    avoid_guard_cell::Bool=true,
    spacing_rule="mean",
)
```

Inspects the mesh to see how far apart faces are in psi_N. Requires that GGD and equilibrium are populated.

Input Arguments:

  * `dd`: a data dictionary instance with required data loaded into it
  * `eq_time_idx`: index of the equilibrium time slice to use. For a typical SOLPS run, the SOLPS mesh will be based on the equilibrium reconstruction at a single time, so the DD associated with the SOLPS run only needs one equilibrium time slice to be loaded. However, one could combine the complete equilibrium time series with the SOLPS run and then have to specify which slice of the equilibrium corresponds to the SOLPS mesh.
  * `eq_profiles_2d_id`x: index of the `profiles_2D` in equilibrium `time_slice`.
  * `grid_ggd_idx`: index of the `grid_ggd` to use. For a typical SOLPS run, the SOLPS grid is fixed, so this index defaults to 1. But in future, if a time varying grid is used, then this index will need to be specified.
  * `space_idx`: index of the space to use. For a typical SOLPS run, there will be only one space so this index will mostly remain at 1.
  * `avoid_guard_cell`: assume that the last cell is a guard cell so take `end-2` and `end-1` instead of `end` and `end-1`
  * `spacing_rule`: "edge" or "mean" to make spacing of new cells (in `psi_N`) be the same as the spacing at the edge of the mesh, or the same as the average spacing
