```
CFETEvolution(reg, start_clock, durations, hamiltonian, options)
```

Create a `CFETEvolution` object.

# Arguments

  * `reg`: a register object.
  * `start_clock`: start clock of the evolution.
  * `durations`: list of durations at each time step.
  * `hamiltonian`: low-level hamiltonian object of type [`Hamiltonian`](@ref).
  * `options`: options of the evolution in type [`KrylovOptions`](@ref).
