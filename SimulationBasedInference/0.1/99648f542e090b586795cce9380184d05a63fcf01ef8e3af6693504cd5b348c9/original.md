```
EnsembleSolver{algType,probType,ensalgType,stateType<:EnsembleState,kwargTypes}
```

Generic implementation of an iterative solver for any ensemble-based algorithm. Uses the SciML `EnsembleProblem` interface to automatically parallelize forward runs over the ensemble.
