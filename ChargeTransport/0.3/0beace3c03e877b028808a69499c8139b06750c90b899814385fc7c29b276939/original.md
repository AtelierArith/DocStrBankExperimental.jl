```julia
electroNeutralSolution(ctsys) -> Any

```

Compute the electro-neutral solution for the Boltzmann approximation. It is obtained by setting the left-hand side in the Poisson equation equal to zero and solving for $\psi$. The charge carriers may obey different statistics functions. Currently, this one is not well tested for the case of charge carriers beyond electrons and holes.
