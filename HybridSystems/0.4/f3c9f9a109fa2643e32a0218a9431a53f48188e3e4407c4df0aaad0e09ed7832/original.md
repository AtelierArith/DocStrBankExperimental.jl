```
GraphAutomaton{GT, ET} <: AbstractAutomaton
```

A hybrid automaton that uses the `Graphs` backend. See the constructor [`GraphAutomaton(::Int)`](@ref).

### Fields

  * `G` – graph of type `GT` whose vertices determine the states
  * `Σ` – dictionary mapping the edges to their labels
