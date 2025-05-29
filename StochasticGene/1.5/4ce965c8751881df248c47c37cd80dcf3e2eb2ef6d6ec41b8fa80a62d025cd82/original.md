```
T_dimension(G, R, S)
T_dimension(G::Tuple, R::Tuple, S::Tuple)
T_dimension(G::Int, R::Int, S::Int)
```

Compute the transition matrix dimension of the GRS model.

# Description

This function computes the transition matrix dimension of the GRS model based on the provided parameters.

# Arguments

  * `G`: Total number of genes or a tuple of total number of genes.
  * `R`: Number of reporters or a tuple of number of reporters.
  * `S`: Number of states or a tuple of number of states.

# Methods

  * `T_dimension(G, R, S)`: Computes the dimension for given integers `G`, `R`, and `S`.
  * `T_dimension(G::Tuple, R::Tuple, S::Tuple)`: Computes the dimension for given tuples `G`, `R`, and `S`.
  * `T_dimension(G::Int, R::Int, S::Int)`: Computes the dimension for given integers `G`, `R`, and `S`.

# Returns

  * `Int`: The dimension of the transition matrix.
