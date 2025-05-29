```
added_mass(panels;kwargs...)
```

Added mass matrix mᵢⱼ = -∫ₛ Φᵢ(x) nⱼ da for a set of `panels`, where Φᵢ is the  potential due to unit motion in direction i. Computation is accelerated with multi-threading when `Threads.nthreads()>1`.
