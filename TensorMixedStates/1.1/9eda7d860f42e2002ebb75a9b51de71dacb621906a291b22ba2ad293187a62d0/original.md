```
Phases = Union{CreateState, SaveState, LoadState, ToMixed, Evolve, Gates, Dmrg, PartialTrace, SteadyState}
```

A type that contains all possible phase types for SimData and runTMS. Each of the types contains at least the three following fields (like SimData).

  * `name`: the name of the phase
  * `time_start`: the simulation time to use at the start of the phase
  * `final_measures`: the measurements to make at the end of the phase see `measure` and `output`
