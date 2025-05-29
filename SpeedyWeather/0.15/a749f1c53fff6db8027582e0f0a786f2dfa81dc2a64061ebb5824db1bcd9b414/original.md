Restart from a previous SpeedyWeather.jl simulation via the restart file restart.jld2 Applies interpolation in the horizontal but not in the vertical. restart.jld2 is identified by

  * `path::String`: path for restart file
  * `id::Union{Int64, String}`: `run_id` of restart file in `run_????/restart.jld2`
