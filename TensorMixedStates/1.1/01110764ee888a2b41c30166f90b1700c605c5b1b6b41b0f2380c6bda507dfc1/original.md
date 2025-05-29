```
Simulation(state[, time = 0])
Simulation(sim, state[, time = sim.time])
```

A type to represent simulation data ans store time and file data. It is used and returned by runTMS. The first form creates a simulation object. The second updates the state in the simulation object. (see also `get_sim_file`)

Most functions applicable to States can be applied to Simulations

# Fields

  * `state`       : the state of the system
  * `time`        : the simulation time
  * `output`      : if not nothing an io where to redirect output
  * `files`       : a dictionary holding io or dict where to write data
  * `formats`     : format info for the output
