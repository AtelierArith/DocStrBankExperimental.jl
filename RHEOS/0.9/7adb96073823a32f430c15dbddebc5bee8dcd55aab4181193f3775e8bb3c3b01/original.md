```
resample(d::RheoTimeData [, t, dt, scale )
```

Resample the data using 1D spline extrapolation (using the Dierckx.jl package).

# Arguments

  * `d`: data as a `RheoTimeData` struct containing time with stress and/or strain. Without additional parameters, the data is resampled to provide a uniform sampling at constant number of timepoints.
  * `t`: an array or range that determines the timepoints where the data will be provided.
  * `dt`: if the array `t` is not provided, the parameter `dt` will set the timestep for a uniform resampling of the data.
  * `scale`: instead of specifying particular time points or timestep, an overall multiplicator on the sampling rate can be provided. This could down-sample (`scale`<1) or upsample (`scale`>1). If timesteps are non uniform, it would interpolate values accordingly.

# Examples

Assuming `d` is a `RheoTimeData` data set:

  * `resample(d)` keeps the number of sampling points the same but interpolates to set a uniform time step.
  * `resample(d, t=-1:0.1:10)` resamples by interpolation to generate a new dataset with time points given by the range `t`.
  * `resample(d, dt=0.1)` resamples by interpolation to generate a new dataset with uniform time step `dt`.
  * `resample(d, scale=2)` resamples by multiplying the sampling rate by 2.
