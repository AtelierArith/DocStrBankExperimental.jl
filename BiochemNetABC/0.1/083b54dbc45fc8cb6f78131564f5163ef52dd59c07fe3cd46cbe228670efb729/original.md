`dist_lp(σ1, σ2; verbose, p, str_stat)`   

Function that computes Lp distance between two trajectories of any dimension. It computes Lp distances for each observed variable (contained in `get_obs_var(σ)`). and then apply a statistic on these distances. Requires `get_obs_var(σ1) == get_obs_var(σ2)`, it is verified if they are simulated from the same model. ...

# Arguments

  * `σ1::AbstractTrajectory` is the first trajectory. σ2 is the second.
  * `verbose::Bool` If `true`, launch a verbose execution of the computation.
  * `str_stat::String` allows to set the statistic to apply on the distances computed  of the trajectories.

Only "mean" is available for now on. ...
