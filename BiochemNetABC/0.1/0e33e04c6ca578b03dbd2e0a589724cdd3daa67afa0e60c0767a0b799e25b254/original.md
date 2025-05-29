`dist_lp(σ1, σ2, var; verbose, p, str_stat)`   

Function that computes Lp distance between two trajectories of any dimension. It computes Lp distances for each observed variable (contained in `get_obs_var(σ)`). and then apply a statistic on these distances. Requires `get_obs_var(σ1) == get_obs_var(σ2)`, it is verified if they are simulated from the same model. ...

# Arguments

  * `σ1::AbstractTrajectory` is the first trajectory. σ2 is the second.
  * `var::Symbol` is an observed variable. Have to be contained in `get_obs_var(σ1)` and `get_obs_var(σ2)`.
  * `verbose::Bool` If `true`, launch a verbose execution of the computation.

...
