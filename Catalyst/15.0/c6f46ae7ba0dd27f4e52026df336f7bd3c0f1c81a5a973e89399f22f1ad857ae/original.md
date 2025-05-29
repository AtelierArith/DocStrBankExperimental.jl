```
laplacianmat(rn::ReactionSystem, pmap=Dict(); sparse=false)
```

Return the negative of the graph Laplacian of the reaction network. The ODE system of a chemical reaction network can be factorized as $\frac{dx}{dt} = Y A_k Φ(x)$, where $Y$ is the [`complexstoichmat`](@ref) and $A_k$ is the negative of the graph Laplacian, and $Φ$ is the [`massactionvector`](@ref). $A_k$ is an n-by-n matrix, where n is the number of complexes, where $A_{ij} = k_{ij}$ if a reaction exists between the two complexes and 0 otherwise.

Returns a symbolic matrix by default, but will return a numerical matrix if parameter values are specified via pmap. 

**Warning**: Unlike other Catalyst functions, the `laplacianmat` function will return a `Matrix{Num}` in the symbolic case. This is to allow easier computation of the matrix decomposition of the ODEs, and to ensure that multiplying the sparse form of the matrix will work.
