```julia
struct Storage{T, N}
```

A `Storage` can be used to store simulation results for a [`Mechanism`](@ref).

Indexing example:     storage.x[body*id][time*step_number][2] # returns the y-position of the specified body at the specified time step.

# Important attributes

  * `x`: Contains the position for each body and each time step.
  * `q`: Contains the orientation for each body and each time step.
  * `v`: Contains the velocity for each body and each time step.
  * `ω`: Contains the angluar velocity for each body and each time step.

# Constructors

```
Storage{T}(step_range, nbodies)
Storage(step_range, nbodies)
Storage{T}(nsteps, nbodies)
Storage(nsteps, nbodies)
```
