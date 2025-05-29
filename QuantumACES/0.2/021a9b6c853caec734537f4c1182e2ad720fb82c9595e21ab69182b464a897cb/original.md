```
calc_memory_distances(c::AbstractCircuit; reset_type::Symbol = :meas_reset, max_event_set_size::Integer = 4, max_edge_degree::Integer = 2, explore_increasing_degree::Bool = false)
```

Calculates the logical Z and X error distances corresponding to the X and Z memory circuits corresponding to the syndrome extraction circuit `c`, which are conventionally the vertical and horizontal distances, respectively. Reset types are specified by `reset_type` and can be `:meas_reset` or `:meas`. Search parameters used by Stim are `max_event_set_size`, `max_edge_degree`, and `explore_increasing_degree`.
