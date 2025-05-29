```
Particles{Backend,N,I,T1,T2} <: AbstractParticles
```

A struct representing a collection of particles.

# Arguments

  * `backend`: The backend used for particle computations (CPUBackend, CUDABackend, AMDGPUBackend).
  * `coords`: Coordinates of the particles
  * `index`: Helper array flaggin active particles
  * `nxcell`: Initial number of particles per cell
  * `max_xcell`: Maximum number of particles per cell
  * `min_xcell`: Minimum number of particles per cell
  * `np`: Number of particles
