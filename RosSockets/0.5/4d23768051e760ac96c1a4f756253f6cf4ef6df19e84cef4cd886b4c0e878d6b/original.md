```
rollout_data(connection::Connection)
```

Get the rollout data from the ROS node. Returns a named tuple of vectors and matrices of the following:

  * ts: vector of times
  * xs: matrix of states (# states by # timesteps)
  * xds: matrix of desired states (# states by # timesteps)
  * us: matrix of control inputs (# inputs by # timesteps)
