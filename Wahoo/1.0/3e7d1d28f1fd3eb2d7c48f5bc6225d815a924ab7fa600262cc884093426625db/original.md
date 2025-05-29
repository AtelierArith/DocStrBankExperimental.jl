Tracks the location of the fish

```
track(;pos_init::Matrix,
       tsave::AbstractVector = 1:100,
       bathymetry::GeoArrays.GeoArray,
       observations::Vector,
       observation_models::Vector{Function},
       sensor_positions::Vector,
       spatial_resolution,
       movement_std,
       save_filter::Bool = false,
       n_trajectories::Int = 0,
       show_progressbar::Bool = !is_logging(stderr),
       precision = Float32)
```

Infers the location of the animal based on a diffusion model and smoothing.

# Keyword Arguments

  * `pos_init::Matrix`: Initial probability distribution of the fish position
  * `tsave::AbstractVector`: Time steps at which the probability map is saved.
  * `bathymetry`: Bathymetric data as `GeoArray`
  * `spatial_resolution`: the spatial resolution [m] of the `bathymetry`.
  * `movement_std`: Standard deviation of the fish movement within one time step [m]
  * `observations`: Vector holding all observations. Each element contains the observation of a separate sensor.
  * `observation_models::Vector{Function}`: Vector containing the observation model for each sensor.
  * `sensor_positions`: Vector of tuples of coordinates or `nothing`, i.e. `Vector{Union{Nothing, Tuple{Real, Real}}}`
  * `save_filter`: if `true` the probabilities from the filter run are returned.
  * `n_trajectories=0`: Number of trajectories to sample
  * `show_progressbar = !is_logging(stderr)`: defaults to `true` for interactive use.
  * `precision = Float32`: numerical floating point type used for computations

Note, the elements of the vectors `observations`, `observation_models`, and `sensor_positions` must be sorted in the same way, i.e. the elements at the same position in the Vectors refer to the same sensor.

# Return

A named tuple with the following elements:

  * `pos_smoother`: Smoothed probability distribution of the fish positions for all timesteps in `tsave`.
  * `residence_dist`: Residence distribution.
  * `trajectories`: Sampled trajectories if `n_trajectories` > 0, otherwise `nothing`.
  * `log_p`: Log probability of the observations.
  * `tsave`: Vector of time steps at which the results are saved.
  * `pos_filter`: Filtered  probability distribution of the fish positions, included if `save_filter = true`.
