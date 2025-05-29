```
SimData(name = "my_simulation", phases::Vector{Phases} = [phase1, phase2...])
```

A type for describing a simulation to use with `runTMS`

# Fields

  * `name`:            the name of the simulation used as the name of the directory to store the results
  * `phases`:          the list of phases of the simulation (see Phases for a list of possible values)
  * `descritpion`:     text put in the description file of the simulation (default "")
  * `time_start`:      initial simulation time (default 0.)
  * `final_measures`:  measures to make at the end of simulation (default []) see `measure` and `output`
  * `time_format`:     C like format for output of simulation time (default "%8.4g")
  * `data_format`:     C like format for output of simulation data (default "%12.6g")
