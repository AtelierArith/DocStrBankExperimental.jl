```
advance_until_stationarity!(TCS::TimeControlSolver, timestep; stationarity_threshold = 1e-11, maxtimesteps = 100, do_after_each_timestep = nothing)
```

Advances a TimeControlSolver in time with the given (initial) timestep until stationarity is detected (change of variables below threshold) or a maximal number of time steps is exceeded. The function do*after*timestep is called after each timestep and can be used to print/save data (and maybe timestep control in future).
