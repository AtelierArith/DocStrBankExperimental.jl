```
MetropolisMonteCarlo(; <keyword arguments>)
```

A Monte Carlo simulator that uses the Metropolis algorithm to sample the configuration space.

# Arguments

  * `temperature::T`: the temperature of the system.
  * `trial_moves::M`: a function that performs the trial moves.
  * `trial_args::Dict`: a dictionary of arguments to be passed to the trial move function.
