Perfect-entanglers distance measure.

```julia
D = D_PE(U; unitarity_weight=0.0, absolute_square=false)
```

For a given two-qubit gate $Û$, this is defined via the [`local_invariants`](@ref) $g_1$, $g_2$, $g_3$ as

$$
D = g_3 \sqrt{g_1^2 + g_2^2} - g_1
$$

This describes the geometric distance of the quantum gate from the polyhedron of perfect entanglers in the Weyl chamber.

This equation is only meaningful under the assumption that $Û$ is unitary. If the two-qubit level are a logical subspace embedded in a larger physical Hilbert space, loss of population from the logical subspace may lead to a non-unitary $Û$. In this case, the [`unitarity`](@ref) measure can be added to the functional by giving a `unitary_weight` ∈ [0, 1) that specifies the relative proportion of the $D$ term and the unitarity term.

By specifying `absolute_square=true`, the functional is modified as $D → |D|²$, optimizing specifically for the *boundary* of the perfect entanglers polyhedron. This accounts for the fact that $D$ can take negative values inside the polyhedron, as well as the `W1` region of the Weyl chamber (the one adjacent to SWAP). This may be especially useful in a system with population loss (`unitarity_weight` > 0), as it avoids situations where the optimization goes deeper into the perfect entanglers while *increasing* population loss.

!!! warning
    The functional does not check which region of the Weyl chamber the quantum gate is in. When using this for an optimization where the guess leads to a point in the `W1` region of the Weyl chamber (close to SWAP), the sign of the functional must be flipped, or else it will optimize for SWAP. Alternatively, use `absolute_square=true`.


!!! tip
    The functional can be converted into the correct form for an optimization that uses one trajectory for each logical basis state by using `QuantumControl.Functionals.gate_functional`.

