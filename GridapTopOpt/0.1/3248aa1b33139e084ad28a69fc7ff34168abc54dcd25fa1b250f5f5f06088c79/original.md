```
reinit!(s::HamiltonJacobiEvolution{O},φ,γ) where O
```

Solve the reinitialisation equation using the `HamiltonJacobiEvolution`.

# Reinitialisation equation

$\frac{\partial\phi}{\partial t} + \mathrm{sign}(\phi_0)(\lVert\boldsymbol{\nabla}\phi\rVert-1) = 0,$

with $\phi(0,\boldsymbol{x})=\phi_0(\boldsymbol{x})$ and $\boldsymbol{x}\in D,~t\in(0,T)$.

# Arguments

  * `s::HamiltonJacobiEvolution{O}`: Method
  * `φ`: level set function as a vector of degrees of freedom
  * `γ`: coeffient on the time step size.
