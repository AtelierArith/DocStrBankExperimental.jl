```
massactionvector(rn::ReactionSystem, scmap = Dict(); combinatoric_ratelaws = true)
```

Return the vector whose entries correspond to the "mass action products" of each complex. For example, given the complex A + B, the corresponding entry of the vector would be $A*B$, and for the complex 2X + Y, the corresponding entry would be $X^2*Y$. The ODE system of a chemical reaction network can be factorized as $rac{dx}{dt} = Y A_k Φ(x)$, where $Y$ is the [`complexstoichmat`](@ref) and $A_k$ is the negative of the [`laplacianmat`](@ref). This utility returns $Φ(x)$.

Returns a symbolic vector by default, but will return a numerical vector if species concentrations are specified as a tuple, vector, or dictionary via scmap.

If the `combinatoric_ratelaws` option is set, will include prefactors for that (see [introduction to Catalyst's rate laws](@ref introduction_to_catalyst_ratelaws). Will default to the default for the system.

**Warning**: Unlike other Catalyst functions, the `massactionvector` function will return a `Vector{Num}` in the symbolic case. This is to allow easier computation of the matrix decomposition of the ODEs.
