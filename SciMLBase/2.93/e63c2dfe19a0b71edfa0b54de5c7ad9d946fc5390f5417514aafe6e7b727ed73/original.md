```julia
struct EnsembleDistributed <: SciMLBase.BasicEnsembleAlgorithm
```

Uses `pmap` internally. It will use as many processors as you have Julia processes. To add more processes, use `addprocs(n)`. These processes can be placed onto multiple different machines in order to paralleize across an entire cluster via passwordless SSH. See Julia's documentation for more details.

Recommended for the case when each trajectory calculation isn't “too quick” (at least about a millisecond each?), where the calculations of a given problem allocate memory, or when you have a very large ensemble. This can be true even on a single shared memory system because distributed process use separate garbage collectors and thus can be even faster than EnsembleThreads if the computation is complex enough.
