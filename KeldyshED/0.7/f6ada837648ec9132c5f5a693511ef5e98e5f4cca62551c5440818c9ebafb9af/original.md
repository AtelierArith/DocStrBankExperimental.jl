```julia
evolution_operator(
    ed::KeldyshED.EDCore,
    grid::Keldysh.AbstractTimeGrid
) -> Vector{Keldysh.GenericTimeGF{ComplexF64, false}}

```

Compute the evolution operator

$$
    \hat S(t, t') = \exp\left(-i \int_{t'}^{t} \hat H d\bar t\right)
$$

on a given contour time grid and represented in the eigenbasis of the Hamiltonian $\hat H$. The operator is returned as a vector of diagonal blocks (matrix-valued Green's function containers) corresponding to invariant subspaces of $\hat H$.
