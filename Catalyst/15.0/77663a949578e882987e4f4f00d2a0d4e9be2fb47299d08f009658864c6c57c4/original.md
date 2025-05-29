```
complexoutgoingmat(network::ReactionSystem; sparse=false)
```

Given a [`ReactionSystem`](@ref) and complex incidence matrix, $B$, return a matrix of size num of complexes by num of reactions that identifies substrate complexes.

Notes:

  * The complex outgoing matrix, $\Delta$, is defined by

$$
\Delta_{i j} = \begin{cases}
    = 0,    &\text{if } B_{i j} = 1, \\
    = B_{i j}, &\text{otherwise.}
\end{cases}
$$

  * Set sparse=true for a sparse matrix representation
