```
simulate!(mechanism, steps, storage, control!;
    record, verbose, abort_upon_failure, opts)

simulate a mechanism

mechanism: Mechanism 
steps: range of steps to simulate 
storage: Storage
control!: Function setting inputs for mechanism
record: flag for recording simulation to storage
verbose: flag for printing during simulation 
abort_upon_failure: flag for terminating simulation is solver fails to meet tolerances
opts: SolverOptions
```
