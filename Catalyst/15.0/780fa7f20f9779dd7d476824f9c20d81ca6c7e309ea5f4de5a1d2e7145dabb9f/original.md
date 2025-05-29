```
adjacencymat(rs::ReactionSystem, pmap = Dict(); sparse = false)

Given a reaction system with n complexes, outputs an n-by-n matrix where R_{ij} is the rate
constant of the reaction between complex i and complex j. Accepts a dictionary, vector, or tuple
of variable-to-value mappings, e.g. [k1 => 1.0, k2 => 2.0,...].

Equivalent to the adjacency matrix of the weighted graph whose weights are the
reaction rates.
Returns a symbolic matrix by default, but will return a numerical matrix if parameter values are specified via pmap.

The difference between this matrix and [`fluxmat`](@ref) is quite subtle. The non-zero entries to both matrices are the rate constants. However:
    - In `fluxmat`, the rows represent complexes and columns represent reactions, and an entry (c, r) is non-zero if reaction r's source complex is c.
    - In `adjacencymat`, the rows and columns both represent complexes, and an entry (c1, c2) is non-zero if there is a reaction c1 --> c2.
```
