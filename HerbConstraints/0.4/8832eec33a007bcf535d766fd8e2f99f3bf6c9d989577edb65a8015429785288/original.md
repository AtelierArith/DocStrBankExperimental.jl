```
GenericSolver
```

Maintains a feasible partial program in a [`SolverState`](@ref). A [`ProgramIterator`](@ref) may manipulate the partial tree with the following tree manipulations:

  * `substitute!`
  * `remove!`
  * `remove_below!`
  * `remove_above!`
  * `remove_all_but!`

Each [`SolverState`](@ref) holds an independent propagation program. Program iterators can freely move back and forth between states using:

  * `new_state!`
  * `save_state!`
  * `load_state!`
