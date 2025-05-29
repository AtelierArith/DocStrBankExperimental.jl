```
evolve!(s::HamiltonJacobiEvolution{O},φ,vel,γ) where O
```

Solve the Hamilton-Jacobi evolution equation using the `HamiltonJacobiEvolution`.

# Hamilton-Jacobi evolution equation

$\frac{\partial\phi}{\partial t} + V(\boldsymbol{x})\lVert\boldsymbol{\nabla}\phi\rVert = 0,$

with $\phi(0,\boldsymbol{x})=\phi_0(\boldsymbol{x})$ and $\boldsymbol{x}\in D,~t\in(0,T)$.

# Arguments

  * `s::HamiltonJacobiEvolution{O}`: Method
  * `φ`: level set function as a vector of degrees of freedom
  * `vel`: the normal velocity as a vector of degrees of freedom
  * `γ`: coeffient on the time step size.
