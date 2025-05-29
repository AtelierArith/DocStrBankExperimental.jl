```
total_energy(system, neighbors=find_neighbors(sys); n_threads=Threads.nthreads())
```

Calculate the total energy of a system as the sum of the [`kinetic_energy`](@ref) and the [`potential_energy`](@ref).
