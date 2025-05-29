```julia
struct EnsembleSerial <: SciMLBase.BasicEnsembleAlgorithm
```

Basic ensemble solver which uses no parallelism and runs the problems in serial
