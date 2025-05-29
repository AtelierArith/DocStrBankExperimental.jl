field*along*trajectory(f,traj::Trajectories,p::Integer[,deriv=0])

Evaluate field `f` (given as grid data) along the trajectory number `p` in the  trajectories specified by `traj`. The output is the history of `f` along this trajectory. If `f` is a vector field, then the component histories are output as a tuple. If `deriv=1`, then it computes the time derivative of the field along the trajectory. The default is `deriv=0` (no derivative).
