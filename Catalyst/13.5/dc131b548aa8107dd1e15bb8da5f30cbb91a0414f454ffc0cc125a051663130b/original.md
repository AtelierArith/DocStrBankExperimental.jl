```
reactioncomplexes(network::ReactionSystem; sparse=false)
```

Calculate the reaction complexes and complex incidence matrix for the given [`ReactionSystem`](@ref).

Notes:

  * returns a pair of a vector of [`ReactionComplex`](@ref)s and the complex incidence matrix.
  * An empty [`ReactionComplex`](@ref) denotes the null (∅) state (from reactions like ∅ -> A or A -> ∅).
  * Constant species are ignored in generating a reaction complex. i.e. if A is constant then A –> B consists of the complexes ∅ and B.
  * The complex incidence matrix, $B$, is number of complexes by number of reactions with

$$
B_{i j} = \begin{cases}
-1, &\text{if the i'th complex is the substrate of the j'th reaction},\\
1, &\text{if the i'th complex is the product of the j'th reaction},\\
0, &\text{otherwise.}
\end{cases}
$$

  * Set sparse=true for a sparse matrix representation of the incidence matrix
