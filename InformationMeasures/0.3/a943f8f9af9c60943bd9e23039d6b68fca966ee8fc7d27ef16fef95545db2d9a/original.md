```
discretize_values(values_x; <keyword arguments>)
```

Assign continuous measurements to discrete bins.

# Arguments

  * `values_x`: the data values.
  * `mode="uniform_width"`: the discretization algorithm.
  * `number_of_bins=0`: the number of bins (will be overridden if `mode` is `"bayesian_blocks"`).
  * `get_number_of_bins=get_root_n`: the method for calculating the number of bins (only called if `number_of_bins` is `0`).
