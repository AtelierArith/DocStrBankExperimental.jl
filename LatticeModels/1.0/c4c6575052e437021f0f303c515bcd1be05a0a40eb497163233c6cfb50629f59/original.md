```
Evolution([solver, ]hamiltonian, states...; timedomain, namedstates...)
```

Create an `Evolution` object that can be used to evolve states in time according to the Schrödinger equation.

# Arguments

  * `solver`: A `EvolutionSolver` object that will be used to evolve the states. If omitted,   a `CachedExp` solver will be created.
  * `hamiltonian`: The Hamiltonian of the system. It can be a matrix, a time-dependent operator   or a function that returns the Hamiltonian at a given time.
  * `states` and `namedstates`: The states to be evolved. They can be `Ket` wavefunctions or   `DataOperator` density matrices.
  * `timedomain`: The time domain to be used for the evolution. If omitted, the non-iterable `Evolution`   object will be returned, and you will be able to call it with   the time domain later.

See `EvolutionSolver` for more information about solvers.

!!! warning
    Please note that the `Evolution` object is a **stateful** iterator. This means that it keeps track of the current time and the states as they evolve. You can perform evolution multiple times, but the timeline will be kept and the states will be updated in place.

    Also do not edit the states in place, as this will affect the evolution. If you need to modify the states or save them, make a copy of them first.

