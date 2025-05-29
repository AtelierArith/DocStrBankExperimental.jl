```
fluxmat(rn::ReactionSystem, pmap = Dict(); sparse=false)
```

Return an r×c matrix $K$ such that, if complex $j$ is the substrate complex of reaction $i$, then $K_{ij} = k$, the rate constant for this reaction. Mostly a helper function for the network Laplacian, [`laplacianmat`](@ref). Has the useful property that $\frac{dx}{dt} = S*K*Φ(x)$, where S is the [`netstoichmat`](@ref) or net stoichiometry matrix and $Φ(x)$ is the [`massactionvector`](@ref).     Returns a symbolic matrix by default, but will return a numerical matrix if rate constants are specified as a `Tuple`, `Vector`, or `Dict` of symbol-value pairs via `pmap`.

**Warning**: Unlike other Catalyst functions, the `fluxmat` function will return a `Matrix{Num}` in the symbolic case. This is to allow easier computation of the matrix decomposition of the ODEs, and to ensure that multiplying the sparse form of the matrix will work.
