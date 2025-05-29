```julia
rank_reveal(energy) -> Tuple{Any, Any}
rank_reveal(energy, order) -> Tuple{Any, Any}

```

Reveal ranks and energies in a specified order.

This function calculates and reveals the ranks and energies of a set of states in either the 'PE' (Projector Energy) or 'EP' (Energy Projector) order.

# Arguments:

  * `energy`: The energy values of states.
  * `order::Symbol`: The order in which to reveal the ranks and energies.

It can be either `:PE` for 'Projector Energy)' order (default) or `:EP` for 'Energy Projector' order.

# Returns:

  * If `order` is `:PE`, the function returns a tuple `(P, E)` where:

      * `P`: A permutation matrix representing projectors.
      * `E`: An array of energy values.
  * If `order` is `:EP`, the function returns a tuple `(E, P)` where:

      * `E`: An array of energy values.
      * `P`: A permutation matrix representing projectors.
