`dist_lp(l_σ1, l_σ2; verbose, p, str_stat_list, str_stat_trajectory)` 

Function that computes Lp distance between two set of any dimensional trajectories. ...

# Arguments

  * `l_σ1::Vector{AbstractTrajectory}` is the first set of trajectories. l_σ2 is the second.
  * `verbose::Bool` If `true`, launch a verbose execution of the computation.
  * `str_stat_list::String` allows to set the statistic to apply on the distances of the trajectories.

It is salso called linkage function in clustering field. Only "mean" is available for now on. ...
