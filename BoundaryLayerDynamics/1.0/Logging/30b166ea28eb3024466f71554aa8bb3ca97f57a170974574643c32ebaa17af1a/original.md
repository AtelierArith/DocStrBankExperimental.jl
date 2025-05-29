```
MeanProfiles(; kwargs...)
```

Collect profiles of terms, averaged over time and horizontal space. The time average is computed with the trapezoidal rule using samples collected before/after each time step. The averages are saved to [HDF5](https://en.wikipedia.org/wiki/Hierarchical_Data_Format) files, which can be written regularly during a simulation.

# Keywords

  * `profiles = (:vel1, :vel2, :vel3)`: Terms of which profiles are collected. Currently supported: `:vel1`, `:vel2`, `:vel3`, `:adv1`, `:adv2`, `:adv3`, `:sgs11`, `:sgs12`, `:sgs13`, `:sgs22`, `:sgs23`, `:sgs33`.
  * `path = "output/profiles"`: Prefix of the path at which HDF5-files with the profiles are saved. The files are numbered, so the first file would be written to `output/profiles-01.h5` for the default path.
  * `output_frequency`: The interval with which the output is written to disk. Note that this should be a multiple of the time step, otherwise some outputs may be skipped.
