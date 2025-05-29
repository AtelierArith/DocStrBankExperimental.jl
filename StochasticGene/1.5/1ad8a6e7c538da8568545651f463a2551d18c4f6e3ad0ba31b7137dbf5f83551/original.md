```
on_states(onstates, G, R, S, insertstep)
on_states(G::Int, R, S, insertstep)
on_states(onstates::Vector, G, R, S)
```

Return vector of on state indices for GR and GRS models.

# Description

This function returns a vector of on state indices for GR and GRS models. It can handle both empty and non-empty `onstates`.

# Arguments

  * `onstates`: Initial onstates. Can be a vector of integers or empty.
  * `G::Int`: Total number of genes.
  * `R`: Number of reporters.
  * `S`: Number of states.
  * `insertstep`: Insert step.

# Methods

  * `on_states(onstates, G, R, S, insertstep)`: Handles both empty and non-empty `onstates`.
  * `on_states(G::Int, R, S, insertstep)`: Generates `onstates` from scratch.
  * `on_states(onstates::Vector, G, R, S)`: Generates `onstates` based on the provided vector.

# Returns

  * `Vector{Int}`: Vector of new onstates.
