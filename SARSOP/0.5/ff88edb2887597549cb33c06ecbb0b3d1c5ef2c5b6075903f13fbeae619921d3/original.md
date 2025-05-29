```
SARSOPSolver
```

Base solver type for SARSOP. Contains an options dictionary with the following entries:

  * 'fast': use fast (but very picky) alternate parser for .pomdp files
  * 'randomization': turn on randomization for the sampling algorithm
  * 'precision': run ends when target precision is reached
  * 'timeout':  [sec] If running time exceeds the specified value, pomdpsol writes out a policy and terminates
  * 'memory': [MB] If memory usage exceeds the specified value, pomdpsol writes out a policy and terminates
  * 'trial-improvement-factor': terminates when the gap between bounds reaches this value
  * 'policy-interval':  the time interval between two consecutive write-out of policy files
  * `verbose`: [true/false] whether to print output from the solver. Default: true
