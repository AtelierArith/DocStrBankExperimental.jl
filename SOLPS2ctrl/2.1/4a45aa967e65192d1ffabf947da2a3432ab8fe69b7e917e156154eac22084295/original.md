```
cached_mesh_extension!(
    dd::IMAS.dd,
    eqdsk_file::String,
    b2fgmtry::String;
    eq_time_idx::Int=1,
    eq_profiles_2d_idx::Int=1,
    grid_ggd_idx::Int=1,
    space_idx::Int=1,
    clear_cache::Bool=false,
)::String
```

Adds an extended mesh to a data dictionary, possibly from a cached result.

Input Arguments:

  * `dd`: The data dictionary. It will be modified in place.
  * `eqdsk_file`: the name of the EQDSK file that was used to get equilibrium data in the dd.
  * `b2fgmtry`: the name of the SOLPS geometry file that was used to get GGD info in `edge_profiles` in the dd.
  * `eq_time_idx`: Index of the time slice in equilibrium
  * `eq_profiles_2d_idx`: Index of the 2D profile set in equilibrium (there is usually only one)
  * `grid_ggd_idx`: Index of the `grid_ggd` set in edge_profiles
  * `space_idx`: Index of the space
  * `clear_cache`: delete any existing cache file (for use in testing)
