A phase type for applying gates

  * `name`: the name of the phase
  * `time_start`: the simulation time to use at the start of the phase
  * `final_measures`: the measurements to make at the end of the phase see `measure` and `output`
  * `limits`: constraints to enforce at each step of the computation
  * `gates`: the gates to apply

# Examples

```
Gates(gates = CNOT(1, 3)*CZ(2,4), limits = Limits(cutoff=1e-10, maxdim = 20))
```
