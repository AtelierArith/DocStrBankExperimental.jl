```
generate_temporal_structure!(m)
```

Create the temporal structure for the given SpineOpt model. After this, you can call the following functions to query the generated structure:

  * `time_slice`
  * `t_before_t`
  * `t_in_t`
  * `t_in_t_excl`
  * `t_overlaps_t`
  * `to_time_slice`
  * `current_window`
