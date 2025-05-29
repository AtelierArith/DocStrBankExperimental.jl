```
mpi_seed!(seed = rand(Random.RandomDevice(), UInt))
```

Re-seed the random number generators in an MPI-safe way. If seed is provided, the random numbers from `rand` will follow a deterministic sequence.

Independence of the random number generators on different MPI ranks is achieved by adding `hash(mpi_rank())` to `seed`.
