```
DEAOptimizer(optimizer; time_limit, silent)
```

An data structure storing the configuration of a DEA optimizer.

# Optimizer specification:

  * `LP`: linear programming default optimizer, GLPK.
  * `NLP`: nonlinear programmin default optimizer, Ipopt.
  * Any JuMP supported solver.

# Optional Arguments

  * `time_limit=:60`: time limit in seconds.
  * `silent=true`: suppress optimizer output.
