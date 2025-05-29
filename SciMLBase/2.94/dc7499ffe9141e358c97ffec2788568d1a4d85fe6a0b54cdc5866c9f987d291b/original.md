```julia
struct EnsembleThreads <: SciMLBase.BasicEnsembleAlgorithm
```

The default. This uses multithreading. It's local (single computer, shared memory) parallelism only. Lowest parallelism overhead for small problems.
