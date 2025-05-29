A phase type to switch to mixed representation

# Fields

  * `name`: the name of the phase
  * `time_start`: the simulation time to use (no much use here)
  * `final_measures`: the measurements to make at the end of the phase see `measure` and `output`

' `limits` : constraints on the final state

# Examples

```
ToMixed()
ToMixed(limits = Limits(cutoff = 1e-10, maxdim = 10))
```
