```
setup_table!(config, data, ::Val{:branch})
```

Sets up the branch table.

  * Flips `f_bus_idx` and `t_bus_idx` so that `f_bus_idx` < `t_bus_idx`
  * Makes bus[:connected*branch*idxs] which contains a vector of the signed index of each branch leaving that bus. (`+` for `f_bus_idx`, `-` for `to_bus_idx`).
