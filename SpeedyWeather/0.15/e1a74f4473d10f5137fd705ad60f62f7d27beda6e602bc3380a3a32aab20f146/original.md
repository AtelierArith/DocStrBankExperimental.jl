Uniform cooling following Paulius and Garner, 2006. JAS. https://doi.org/10.1175/JAS3705.1 imposing a default temperature tendency of -1.5K/day (=1K/16hours for a `time_scale` of 16 hours) on every level except for the stratosphere (diagnosed as `temp < temp_min`) where a relaxation term with `time_scale_stratosphere` towards `temp_stratosphere` is applied.

```
dT/dt = -1.5K/day for T > 207.5K else (200K-T) / 5 days
```

Fields are

  * `time_scale::Dates.Second`: [OPTION] time scale of cooling, default = -1.5K/day = -1K/16hrs
  * `temp_min::Any`: [OPTION] temperature [K] below which stratospheric relaxation is applied
  * `temp_stratosphere::Any`: [OPTION] target temperature [K] of stratospheric relaxation
  * `time_scale_stratosphere::Dates.Second`: [OPTION] time scale of stratospheric relaxation
