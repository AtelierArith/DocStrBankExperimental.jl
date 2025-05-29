```
fill_in_extrapolated_core_profile!(
    dd::IMAS.dd,
    quantity_name::String;
    method::String="simple",
    eq_time_idx::Int=1,
    eq_profiles_2d_idx::Int=1,
    grid_ggd_idx::Int=1,
    space_idx::Int=1,
)
```

This function accepts a DD that should be populated with `equilibrium` and `edge_profiles` as well as a request for a quantity to extrapolate into the core. It then maps `edge_profiles` data to rho, calls the function that performs the extrapolation (which is not a simple linear extrapolation but has some trickery to attempt to make a somewhat convincing profile shape), and writes the result to core_profiles. This involves a bunch of interpolations and stuff.

Input arguments:

  * `dd`: an IMAS data dictionary
  * `quantity_name`: the name of a quantity in `edge_profiles.profiles_2d` and `core_profiles.profiles_1d`, such as "electrons.density"
  * `method`: Extrapolation method.
  * `eq_time_id`x: index of the equilibrium time slice to use. For a typical SOLPS run, the SOLPS mesh will be based on the equilibrium reconstruction at a single time, so the DD associated with the SOLPS run only needs one equilibrium time slice to be loaded. However, one could combine the complete equilibrium time series with the SOLPS run and then have to specify which slice of the equilibrium corresponds to the SOLPS mesh.
  * `eq_profiles_2d_idx`: index of the `profiles_2D` in equilibrium `time_slice`.
  * `grid_ggd_idx`: index of the `grid_ggd` to use. For a typical SOLPS run, the SOLPS grid is fixed, so this index defaults to 1. But in future, if a time varying grid is used, then this index will need to be specified.
  * `space_id`x: index of the space to use. For a typical SOLPS run, there will be only one space so this index will mostly remain at 1.
  * `cell_subset_idx`: index of the subset of cells to use for the extrapolation. The default is 5, which is the subset of all cells. If `edge_profiles` data is instead present for a different subset, for instance, -5, which are b2.5 cells only, then this index should be set to -5.
